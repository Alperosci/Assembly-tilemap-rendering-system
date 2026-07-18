# MISA Tilemap Renderer

A tilemap rendering engine written in assembly language for the MISA architecture (Mnemonimov Assembly).

This project demonstrates a simple tile-based rendering system implemented entirely in assembly. 
The renderer reads map data stored as raw byte arrays and converts tile values into drawable objects.

## Features

- Written entirely in MISA assembly
- Tilemap-based rendering system
- Supports custom map data stored in memory
- Configurable map dimensions
- Simple binary tile format (`0` = empty, `1` = solid tile)

## How to run

Create a new directory inside Mnemonimov's user_projects folder and clone this repository into it.

## Map Format

Maps are stored as arrays of `u8` values:

```
1,1,1,1
1,0,0,1
1,0,1,1
1,1,1,1
```

Each value represents a tile:

| Value | Meaning |
|-------|---------|
| `0` | Empty space |
| `1` | Rendered tile |

## Configuration

Map size and tile size can be configured:

```asm
def WIDTH 32
def HEIGHT 24
def TILESIZE 10
```

The renderer calculates the total amount of tiles automatically:

```asm
def TOTAL_TILES WIDTH*HEIGHT
```

## Rendering Process

The renderer:

1. Initializes a pointer to the map data.
2. Iterates through every tile.
3. Checks the tile value.
4. Converts the tile index into an X/Y position.
5. Draws the tile using the MISA graphics system call.

Example:

```asm
mod s2, s0, WIDTH   # X coordinate
div s2, s0, WIDTH   # Y coordinate
```

## Example Maps

The project includes multiple test maps:

- `sq` - Simple square pattern
- `sq2` - Circle-like pattern
- `sq3` - Filled shape test
- `lettera` / `letterb` - Character rendering tests
- `fullsizetesting` - Full 32x24 map test
- `maze` - Maze rendering test
