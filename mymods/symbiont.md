Test
```julia:ex
using WGLMakie, JSServe
io = IOBuffer()
println(io, "~~~")
show(io, MIME"text/html"(), Page(exportable=true, offline=true))
app = JSServe.App() do
    return DOM.div(
        WGLMakie.scatter(1:4),
        WGLMakie.surface(rand(4, 4))
    )[]
end
show(io, MIME"text/html"(), app)
println(io, "~~~")
println(String(take!(io)))
```
\textoutput{ex}