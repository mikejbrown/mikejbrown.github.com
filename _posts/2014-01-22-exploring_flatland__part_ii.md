---
layout: post
title: 'Exploring Flatland: Part II'
date: 2014-01-22 02:13:00
---

[Last time]({% post_url 2014-01-13-exploring_flatland__part_i %}) we introduced
the idea of a two dimensional world, or 2+1 if we're including time as a
dimension (as we should). I said that this time we would look at orbits, and I
also said that long range forces go off as \\( 1/r \\) rather than \\( 1/r^2 \\)
as they do in our universe, but I never justified that. Let's take a brief foray
into field theory to justify it, then come back to the orbital mechanics problem.

## Potential energy

In Newtonian gravity and electrostatics the force law is given by the simplest
possible field theory there can be. There is a thing called the *potential* -
gravitational or electric potential depending on the context - which assigns a
simple number to every point in space. This is an example of a *scalar field*.
The scalar field responds to mass or charge (for gravitation, electricity resp.)
by changing from place to place, and particles are subject to a force
proportional to the gradient of the field at the location of the particle.

So how is the field sourced by matter? Lorentz invariance and the requirement
that the field equation is linear in the field and second order (both minimality
assumptions) fix the field equation as

$$ \left( \frac{1}{c^2} \frac{\partial^2}{\partial t^2} - \nabla^2 + \frac{\mu^2 c^2}{\hbar^2} \right) \phi = - \rho, $$

where \\( \rho \\) is the source density. We'll derive this equation when we
come to field theory properly. It is the *Klein-Gordon equation* (with a source
term). This may look scary to the un-initiated, but believe me this equation is
actually dead easy to solve (the solutions with rotational symmetry even have a
name: they're Bessel functions). If I can reduce a problem to this equation I'm
very happy. It is also very easy to make this equation impossible to solve by
adding some very simple terms that have interesting physics behind them, but we
won't get into that now. We made those minimality assumptions because it makes
the equation linear and hence solvable, but they are justifiable because *small
perturbations* to any system are generically linear. We imagine that the true
theory of the world could be something very complicated, but we are only trying
to understand small disturbances to one part of it so we can work instead with a
dramatically simplified version of things. The beauty of physics is you can
often make progress this way, unlike in, say, economics.

I didn't explain what \\(\mu\\) is. It is a physical constant of the scalar field
theory with units of mass. When we get to quantum field theory it turns out the
be the mass of the *particles* associated with the \\(\phi\\) field! But for now
it's just a number. Our general requirements on the field equation don't fix
it's value. But if \\(\mu\neq 0\\) it turns out the force carried by the
\\(\phi\\) field is *short ranged*, meaning it dies off exponentially with
\\(r\\) over a length scale \\( \hbar / mc \\). So to get a long range force,
falling off as a power law, we take \\(\mu=0\\).

So we study the case \\(\mu=0\\) and with a static point source at the origin
(representing something like a point particle, or a planet from far away). Thus
there is circular symmetry and we have

$$ \frac{1}{r} \frac{\partial}{\partial r} \left( r \frac{\partial}{\partial r} \phi \right) = 0, $$

up to the delta function source at the origin which we will account for shortly.
If we multiply both sides by \\(r\\) and integrate once we get

$$ r \frac{\partial}{\partial r} \phi = k, $$

for some constant \\(k\\) which will be somehow related to the source strength.
Now divide by \\(r\\) and integrate to get the field generated by a point
source:

$$ \phi(r) = k \ln\left(\frac{r}{\ell}\right), $$

where the length scale \\(\ell\\) is the other required integration constant.

To fix the normalisation we go back to the equation of motion and integrate over
space using the divergence theorem:

$$ \begin{align}
\int \mathrm{d}^2 x \rho & = \int \mathrm{d}^2 x \nabla^2 \phi \\\\
 & = \int \mathrm{d}\vec{\Omega} \cdot \nabla \phi \\\\
 & = \int \mathrm{d}\theta\ r\partial_r \phi \\\\
 & = 2\pi k.
\end{align} $$

So if we call the total source \\(q \equiv \int\mathrm{d}^2 x \rho\\) then

$$ \phi(r) = \frac{q}{2\pi} \ln\left(\frac{r}{\ell}\right). $$

So that's the field. The interaction potential energy of a particle with charge
\\(q'\\) is \\( U = q' \phi \\). This is the potential energy we will use to
work out the orbital mechanics.

## Orbital mechanics

Already we can see something that marks a very important difference between 2+1D
and 3+1D: the interaction potential grows without bound as \\( r \to \infty \\).
This means that two particles which are attracted cannot be separated. This is
in contrast to our universe where the potential goes as \\( 1/r \to 0 \\) as the
separation goes to infinity. This means that, for example, a rocket can reach
escape velocity and leave the Earth. The energy cost to do a similar thing in
Flatland could be much greater, and you would never truly "escape", although
with enough energy you could reach an arbitrarily great distance before falling
back down.

Let's see if any more surprises are in store. Much of what you do when you tackle
the Newtonian two body problem back in first year (or whenever you do it where
you come from) remains valid. You can dis-entangle the centre of mass and
relative motion of the two bodies, and the centre of mass motion is free because
of the total internal force on the system is zero (that's the action-reaction
thing: one of Newton's laws, but I can never remember which one) and we don't have
any externally applied forces. For the relative motion you just have a central
force problem where instead of the actual mass of either particle you use the
reduced mass \\( \mu = \frac{m_1 m_2}{m_1 + m_2} \\). Don't confuse this with
the constant in the Klein-Gordon equation from before! As usual this trick accounts
for the fact that the bodies in fact revolve around their common centre of mass
instead of around each other.

Now it's easiest to derive the equations of motion from the Lagrangian written
in polar coordinates[^1]:

$$ L = \frac{1}{2} \mu \dot{r}^2 + \frac{1}{2} \mu r^2 \dot{\theta}^2 -
\frac{q_1 q_2}{2\pi} \ln\left(\frac{r}{\ell}\right). $$

The \\(\theta\\) coordinate is cyclic, meaning angular momentum is conserved as
expected. Writing \\( J \equiv \mu r^2 \dot{\theta} \\) we get the radial equation
of motion as

$$ \mu \ddot{r} = \frac{J^2}{\mu r^3} - \frac{q_1 q_2}{2\pi r}, $$

which can just as well be derived from the effective Lagrangian

$$ L_\text{eff} = \frac{1}{2} \mu \dot{r}^2 - U_\text{eff}\left(r\right), $$

with the effective potential

$$ U_\text{eff}\left(r\right) = \frac{J^2}{2\mu r^2} + \frac{q_1
q_2}{2\pi}\ln\left(\frac{r}{\ell}\right). $$

This should all look rather like the standard Kepler problem: a centrifugal
repulsion (yes, it's real) and an attractive potential due to the force. The
only real difference is the \\(\ln r\\) instead of \\( 1/r \\). It gets more
interesting when we solve the equations of motion. To make it easier we start
with perfectly circular orbits. You get these at the minimum of \\( U_\text{eff} \\)
, given by \\( r_0^2 \equiv \frac{2\pi J^2}{q_1 q_2 \mu} \\). The angular
velocity in this case is constant, so we can easily find the period of the
orbit:

$$ T_0 = \frac{2\pi}{\dot{\theta}} = \frac{4\pi^2 J}{q_1 q_2}. $$

Now we can simplify the equations of motion by choosing natural units. We take
\\( r_0 \\) as the unit of distance and \\( \tau \equiv T_0 / 2\pi \\) as the
natural unit of time. Defining the dimensionless radius \\( \rho \equiv r / r_0 \\)
and the time derivative \\( f' \equiv \tau \dot{f} \\) we get

$$\begin{align}
\rho'' &= \frac{1}{\rho^3} - \frac{1}{\rho} \\
\theta' &= \frac{1}{\rho^2}
\end{align}$$

Before solving these equations numerically we want to see where we can get
analytically. A circular orbit corresponds to \\( \rho = 1 \\), but what if the
orbit is slightly disturbed from a circular one? First of all it is stable,
because the circular orbit is a _minimum_ rather than a maximum of the effective
potential. But does the orbit close? What is its shape?

To find out we Taylor expand the right hand side of the radial equation in
\\( \delta\rho = \rho -1\\), getting \\(\delta\rho'' = -2 \delta\rho + \cdots\\).
Thus the radial coordinate oscillates about the circular orbit position with a
frequency of \\( \sqrt{2} \\) in natural units. This means that the orbit
doesn't close on itself: it returns to its original radius well _before_ it has
gotten all the way around the orbit. In fact, since \\(\sqrt{2}\\) is irrational
the body **never returns to a previous state**. Instead, over time, its path
passes arbitrarily close to any point of the ring between the limits of its orbit
$$ \rho_\text{min} \le \rho \le \rho_\text{max} $$! (Note that this precise
relation between periods only holds for near circular orbits.)

We can see this explicitly by numerically solving the equations of motion. This
is a simple task (on my computer it takes under five seconds to do the
calculation, while running heaps of other stuff including a video and a couple
of heavily loaded web browsers, and it takes a hundred seconds to export the
result to an animated gif!!) and here is an animation of a slightly disturbed
orbit:

![slightly disturbed orbit](/images/flatland_2_post/orbit1.gif)
{: style="width: 360px"}

Things are clearer for even more disturbed orbits:

![badly non-circular orbit](/images/flatland_2_post/orbit2.gif)
{: style="width: 360px"}

The orbit looks more like a precessing trefoil than an ellipse! This would have
huge implications for the development of Flatlander astronomy and probably
science more broadly (*if* they live in a planetary system!). It was the fact that
regular cycles appear on the sky that led to an understanding of time keeping and
our place in the universe. Only by observing astronomical regularities were the
foundations laid for the revolution brought on by the likes of Kepler, Galileo and
Newton. It is hard to imagine how Flatlander society would develop. Navigating by
the stars is certainly a non-starter.  Would they ever rise above the brute fear
of wild and capricious elements to discover the hidden patterns underlying their
world? 

[^1]:
    If you've not seen Lagrangian mechanics _don't panic_: this
    is a very compact way of doing problems that are hard to do by Newton's laws
    directly, and is in fact the right way to think about classical mechanics if you
    want to generalise it to quantum mechanics. It is more second nature to me now,
    so much so that I have to think a bit about whether I'm applying Newton's
    laws correctly when I'm not working from a Lagrangian. You won't learn Lagrangian
    mechanics from my brief sketch here though. Look around the web for help.
