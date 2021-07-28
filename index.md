@def title = "Franklin Example"
@def tags = ["syntax", "code"]

# The Outside of the Assylum

\tableofcontents <!-- you can use \toc as well -->

Just a random collection of bits n' bobs. Some [solutions to problems](/menu1/) from maths text books. Bayesian data analyis [demos](/menu3/) being ported from R to Julia. And models from my [research](/menu2/).

Also, this [nonsesense MWE](/MWE/index.html)

```julia:ex
using Pkg
Pkg.activate("..//pkgs")
using WGLMakie, JSServe
WGLMakie.activate!()
io = IOBuffer()
fig(o) = show(io, MIME"text/html"(), o)
println(io, "~~~")
Page(exportable=true, offline=true) |> fig
scatter(1:4) |> fig
surface(rand(4, 4)) |> fig
JSServe.Slider(1:3) |> fig
println(io, "~~~")
println(String(take!(io)))
```
\textoutput{ex}
