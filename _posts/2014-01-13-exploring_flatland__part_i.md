---
layout: post
title: 'Exploring Flatland: Part I'
date: 2014-01-13 22:04:00
excerpt: "If you haven't read Edwin Abbott's *[Flatland: A Romance of Many
  Dimensions](https://en.wikipedia.org/wiki/Flatland)* go and read it now. It is
  now in the public domain so it's free online, and your geek cred will go up by
  500 points."
---

##  Intro

If you haven't read Edwin Abbott's
*[Flatland: A Romance of Many
Dimensions](https://en.wikipedia.org/wiki/Flatland)* go and read it now. It is
now in the public domain so it's free online, and your geek cred will go up by
500 points. Reading it as a kid it is a fun and mind-expanding adventure into
the world of creatures of different dimensionality. Reading it as an adult it is
a brilliant satire of Victorian society. I remember experiencing it as both.

As a physicist I'm taken with the idea of imagining what the world would be like
without a third dimension to climb around in. I'm also inspired with the great
work Greg Egan has done with his
[Orthogonal](http://gregegan.customer.netspace.net.au/ORTHOGONAL/ORTHOGONAL.html)
series: taking hard sci-fi to its limit by working out what physics *really
would be like* in his imagined (Euclidean rather than Minkowskian) world. The
results are both strangely familiar to and strangely different from our world, and 
rich enough to provide the backdrop for a meaningful story. So with this series
I would like to take a stab at a similar thing for Flatland.

What would physics be like if the world were two dimensional? (Or 2+1
dimensional, really, including time as a dimension.) There are some remarkable
consequences from this simple change. For example, we will find that:

* There is no such thing as a long range gravitational force.
* All attractive forces are *confined*: any two particles which are attracted to
  each other are *permanently* bound. There is no pulling them apart, and at
  large enough scales all you ever see are very weakly interacting neutral
  composites.
* A large class of phase transitions are impossible.
* Permanent vortices can exist.
* Particles can have any amount of spin, and can have "topological order" -
  properties of the whole system greater than the sum of its parts, and stable
  against outside disturbances - due to quantum weirdness.

It's going to be hard going to get any decent story prospects, but the journey
itself might be a little fun. And who knows... there may be life here. But it's
definitely not life as we know it.

## Mechanics

Not much happens to ordinary mechanics when you get rid of a dimension. The same
conservation laws still work. The main difference is that angular momentum is a
scalar. The cross product of two vectors \\(\vec{u}=(u_x,u_y,u_z)\\) and
\\(\vec{v}=(v_x,v_y,v_z)\\):

$$ \vec{u}\times\vec{v} = (u_y v_z - u_z v_y, u_z v_x - u_x v_z, u_x v_y - u_y
v_x). $$

Clearly the only component that makes any sense in two dimension is the last
one: \\( u_x v_y - u_y v_x \\). The fact that this transforms as a scalar under
rotations in the plane follows from the fact that \\(\vec{u}\times\vec{v}\\)
transforms like a vector under three dimensional rotations.

The physical reason behind this mathematical fact is that cross products always
have to do with rotations, and rotations are really described by a plane rather
than an axis. It just so happens that in three dimensions every plane has a
unique (up to sign) vector pointing perpendicular to it, so you can get away with
talking about vector cross products. This concept doesn't generalise to different
dimensionality. Rotations, curls etc. are better understood in terms of a rank-2
antisymmetric tensor. Only in three dimensions does the number of components of
one of these, \\( \frac{D(D-1)}{2} \\), equal the number of dimensions of a vector
\\( D \\), and an invariant tensor \\( \epsilon_{ijk} \\) exists which lets you
identify an antisymmetric tensor with a vector:

$$ \left(\vec{u}\times\vec{v}\right)_i = \sum_{jk} \epsilon_{ijk} u_j v_k. $$

If you keep this one thing in mind then all of the other stuff in mechanics
(Newton's laws, conservation of energy, momentum, angular momentum, torques,
rigid body mechanics etc. etc.) all follows through without any real surprises.
The interesting stuff come when we get to quantum mechanics and field theory.

In the next installment we'll assume for the moment that gravity still exists
and falls off as \\( 1/r \\) and have a go at the Kepler problem to see what
orbits are like. When we get to general relativity we'll see that, in fact,
there is no gravitational force in flatland, but the force law we derive will
still be valid for a force mediated by a massless scalar field, or in the
non-relativistic limit of electromagnetism.
