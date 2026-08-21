# IFAC 2026 Workshop: Hands-on Notebooks

Runnable notebooks from **GPU Acceleration in Optimization and Optimal
Control**, pre-congress workshop WS-12 at the 23rd IFAC World Congress
(BEXCO, Busan, Sunday 23 August 2026).

Workshop page, lecture slides, and rendered notebooks:
<https://madsuite.org/ifac2026/>

| Notebook | Contents |
|---|---|
| `1-gpu-computing.ipynb` | GPU computing in the Julia language: arrays, broadcasting, reductions, linear algebra, KernelAbstractions.jl kernels, batched simulation |
| `2-optimal-control-and-estimation.ipynb` | Direct transcription, pendulum swing-up, Goddard's rocket by orthogonal collocation, particle steering, parameter estimation for the Boehm STAT5 model |
| `minimum-time-solution.ipynb` | Worked solution to the minimum-time swing-up exercise |
| `particle-steering-solution.ipynb` | Worked solution to the particle steering exercise |

The committed outputs are real runs from the workshop's GPU servers
(NVIDIA Quadro GV100).

## Running them yourself

The GPU parts need an NVIDIA GPU; the CPU parts (Ipopt solves, plotting)
run anywhere. During the workshop itself, a hosted notebook server with
this environment preinstalled is provided in the room, so none of this
setup is needed there.

1. Install [Julia](https://julialang.org/downloads/) 1.12.

2. Instantiate the project environment ([`Project.toml`](Project.toml)
   pins the package versions the notebooks were executed with):

   ```bash
   julia --project=. -e 'using Pkg; Pkg.instantiate()'
   ```

3. Install the Jupyter kernel, pointed at this environment:

   ```julia
   using Pkg; Pkg.add("IJulia")
   using IJulia
   installkernel("julia-ifac2026", "--project=@.")
   ```

4. Start Jupyter in this directory and select the `julia-ifac2026`
   kernel:

   ```bash
   jupyter lab
   ```

The notebooks read `boehm_data.jl` and `figs/` by relative path, so run
them from this directory.

## License

MIT
