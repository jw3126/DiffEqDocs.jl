# SDE Types

## Mathematical Specification of a SDE Problem

To define an SDE Problem, you simply need to give the forcing function ``f``,
the noise function `g`, and the initial condition ``u₀`` which define an SDE

```math
du = f(t,u)dt + Σgᵢ(t,u)dWⁱ
```

`f` and `g` should be specified as `f(t,u)` and  `g(t,u)` respectively, and `u₀`
should be an AbstractArray whose geometry matches the desired geometry of `u`.
Note that we are not limited to numbers or vectors for `u₀`, one is allowed to
provide `u₀` as arbitrary matrices / higher dimension tensors as well. A vector
of `g`s can also be defined to determine an SDE of higher Ito dimension.

## Problem Type

Wraps the data which defines an SDE problem

```math
u = f(u,t)dt + Σgᵢ(u,t)dWⁱ
```

with initial condition ``u0``.

### Constructors

`SDEProblem(f,g,u0,tspan,noise=WHITE_NOISE)` : Defines the SDE with the specified
functions. The default noise is `WHITE_NOISE`.

### Fields

* `f`: The drift function in the SDE.
* `g`: The noise function in the SDE.
* `u0`: The initial condition.
* `tspan`: The timespan for the problem.
* `noise`: The noise process applied to the noise upon generation.

## Noise Processes

## Special Solver Options

## Special Solution Fields

* `g`: The noise function in the SDE.

## Example Problems

Examples problems can be found in [DiffEqProblemLibrary.jl](https://github.com/JuliaDiffEq/DiffEqProblemLibrary.jl/blob/master/src/sde_premade_problems.jl).

To use a sample problem, such as `prob_sde_linear`, you can do something like:

```julia
# Pkg.add("DiffEqProblemLibrary")
using DiffEqProblemLibrary
prob = prob_sde_linear
sol = solve(prob)
```

```@docs
DiffEqProblemLibrary.prob_sde_linear
DiffEqProblemLibrary.prob_sde_2Dlinear
DiffEqProblemLibrary.prob_sde_wave
DiffEqProblemLibrary.prob_sde_lorenz
DiffEqProblemLibrary.prob_sde_cubic
DiffEqProblemLibrary.prob_sde_additive
DiffEqProblemLibrary.prob_sde_additivesystem
```
