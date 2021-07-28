@def title = "Franklin Example"
@def tags = ["syntax", "code"]

# The Outside of the Assylum

\tableofcontents <!-- you can use \toc as well -->

Just a random collection of bits n' bobs. Some [solutions to problems](/menu1/) from maths text books. Bayesian data analyis [demos](/menu3/) being ported from R to Julia. And models from my [research](/menu2/).

Also, this [nonsesense MWE](/MWE/index.html)

```julia:./code/ex1
using WGLMakie, JSServe
io = IOBuffer()
println(io, "~~~")
show(io, MIME"text/html"(), Page(exportable=true, offline=true))
app = JSServe.App() do
    return DOM.div(
        scatter(1:4),
        surface(rand(4, 4)),
        JSServe.Slider(1:3)
    )
end
show(io, MIME"text/html"(), app)
println(io, "~~~")
println(String(take!(io)))
```

