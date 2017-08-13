# cairo-canvas [![Hackage version](https://img.shields.io/hackage/v/cairo-canvas.svg?style=flat)](https://hackage.haskell.org/package/cairo-canvas) [![Build Status](https://travis-ci.org/apirogov/cairo-canvas.svg)](https://travis-ci.org/apirogov/cairo-canvas)

Haskell library providing an alternative drawing API for Cairo
which is heavily inspired by [Processing](https://processing.org/reference).

##### Install

This library depends on the [cairo bindings](https://hackage.haskell.org/package/cairo).

You also need the [SDL2 bindings](http://hackage.haskell.org/package/sdl2), if you want to build the demo.

Just clone and install this repository:
```bash
git clone git@github.com:apirogov/cairo-canvas.git
cd cairo-canvas
stack install
```

It should work with recent GHC versions (>= 7.8.4) without problems under Linux und OS X.

##### Documentation

Generate the haddock documentation for reference.

```haskell
import SDL.Cairo
import Graphics.Rendering.Cairo.Canvas
...
  texture <- createCairoTexture renderer (V2 800 600)
  withCairoTexture' texture $ runCanvas $ do
    background $ gray 100
    stroke $ red 255
    fill $ blue 255 !@ 128
    rect $ D 0 0 100 100
    rect $ toD (V2 50 50) (V2 150 150)

  copy renderer texture Nothing Nothing
  present renderer
```

See the source of Main.hs for more examples. You start that demo with:
```bash
stack install --flag cairo-canvas:builddemo
stack exec cairo-canvas-test
```
