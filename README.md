# CostyCNC Stroke Foam Cutter

**Create clean 2D contours for hot-wire foam cutting from an image — without CAD/CAM software.**

This repository contains the source code for the **CostyCNC Stroke Foam Cutter**, a browser-based tool that converts an image of text or a shape into an SVG contour that can be used as the basis for **hot-wire foam cutting**.

It is especially useful for people who want to cut **EPS, XPS, polystyrene, foam, and similar lightweight foam materials** but do not want to start with a CAD/CAM workflow.

The project is part of the CostyCNC software ecosystem.

## What problem does it solve?

Creating a cutting contour from an image can normally involve several steps:

**image → vectorization → contour adjustment → SVG → G-code → CNC cutting**

For simple foam-cutting projects, that workflow can be unnecessarily complicated.

CostyCNC Stroke Foam Cutter provides a much simpler approach:

**image → contour → SVG → G-code → foam cutter**

You can start from an image containing **text, a logo, a silhouette, or another black-and-white shape**, adjust the contour directly in the browser, and save the resulting SVG.

## What can you do with it?

The application can:

- open an image from your computer
- process the image in the browser
- convert the image into vector paths using a JavaScript implementation of Potrace
- add or adjust a **stroke around the generated path**
- change the stroke width
- choose between an outlined contour and a filled shape
- combine the generated result into **one path**
- zoom the result
- move the generated text/shape
- save the result as SVG
- save the result as PNG
- copy the generated PNG representation to the clipboard
- paste an image directly from the clipboard

The goal is not to replace a full CAD system.

The goal is to make **simple 2D foam-cutting contours accessible without CAD/CAM skills**.

## How it works

### 1. Start with an image

Load an image containing the shape or text you want to cut.

The source can be a simple raster image such as a black-and-white drawing, silhouette, logo, or text.

You can also paste an image from the clipboard.

### 2. Convert the image to a path

The project uses the included `potrace.js` code to convert the raster image into SVG paths.

Potrace performs the bitmap-to-vector conversion and produces smooth curves and corners.

### 3. Adjust the contour

Use the **Stroke** control to change the width of the contour.

The application can display the result as:

- a black filled shape
- a black outline with adjustable stroke width
- a single combined path when the **one path** option is enabled

This is useful when the desired cutting line needs to be larger or smaller than the original image boundary.

### 4. Save the SVG

The generated SVG can then be used as an intermediate drawing format for the next step of a CNC workflow.

For CostyCNC users, the SVG can be converted into G-code with the CostyCNC image-to-G-code tool.

## From image to G-code

This repository itself generates the **SVG contour**. It does not directly generate the CNC G-code.

The next step can be performed with the CostyCNC G-code generator:

**Image → Stroke Foam Cutter → SVG → CostyCNC G-code generator → G-code → foam cutter**

The CostyCNC G-code generator is available at:

**https://www.costycnc.it/cm8**

This separation is intentional: the Stroke Foam Cutter is the **image and contour preparation step**, while the G-code generator handles the CNC toolpath.

## Why use a stroke?

A raster image describes pixels and areas.

A foam cutter needs a **cutting path**.

The stroke operation lets you control the visible contour around the generated vector path. This is useful for turning an image or text shape into a practical cutting outline.

For example, a text image can be converted into a vector contour and then given a wider stroke before being exported as SVG.

## Example workflow

A simple workflow can be:

1. Create or find an image of the desired shape.
2. Open it in CostyCNC Stroke Foam Cutter.
3. Adjust **Stroke**.
4. Select **fill** if a filled shape is needed.
5. Select **one path** when a single path is desired.
6. Adjust zoom or position if necessary.
7. Save the SVG.
8. Open the SVG in the CostyCNC G-code generator.
9. Generate G-code.
10. Send the G-code to a compatible foam-cutting CNC.

## Technology

The project is a client-side web application using:

- **HTML**
- **JavaScript**
- **SVG**
- **Canvas**
- **Potrace**

The included `potrace.js` is a JavaScript implementation of the Potrace bitmap-to-vector algorithm.

The image processing happens in the browser. The application generates the SVG result directly on the client side.

## Repository structure

```text
costycnc-stroke-foam-cutter/
├── README.md
├── index.html
└── potrace.js
```

### index.html

Contains the web interface and the application logic.

It handles:

- image loading
- clipboard image input
- SVG display
- stroke adjustment
- fill / outline selection
- one-path mode
- zoom
- positioning
- SVG export
- PNG export

### potrace.js

Contains the JavaScript Potrace implementation used to convert raster images into SVG paths.

## Who is this for?

This project is useful for:

- foam model makers
- sign makers
- theater and decoration projects
- DIY makers
- hobby CNC users
- EPS/XPS foam cutters
- people creating foam letters
- people creating simple foam silhouettes
- beginners who do not know CAD/CAM
- CostyCNC users preparing SVG contours for foam cutting

It is particularly useful when the starting point is an **image rather than a CAD drawing**.

## What this project is not

This is not a general-purpose CAD program.

It is not a complete CAM system.

It does not directly calculate a complete CNC toolpath or replace the G-code generation stage.

It is a focused tool for one part of the workflow:

**turning an image into an editable SVG contour for foam cutting.**

## CostyCNC approach

The idea behind this project is simple:

**Do not force a beginner to learn a complete CAD/CAM workflow when a simple image is enough to create the desired foam contour.**

The project therefore sits between the image and the CNC stages:

**Image → SVG contour → G-code → foam cutting**

That makes it possible to build a practical workflow from simple tools instead of requiring a complex CAD/CAM application from the beginning.

## Related CostyCNC tool

After creating the SVG contour, use the CostyCNC G-code generator to convert the drawing into CNC G-code:

**https://www.costycnc.it/cm8**

The Stroke Foam Cutter and the G-code generator are separate tools with different jobs.

## Search terms

This repository is relevant to searches such as:

- foam cutter from image
- hot wire foam cutter SVG
- create foam cutting contour from image
- image to SVG for foam cutter
- EPS foam cutting SVG
- XPS foam cutting SVG
- polystyrene foam cutter contour
- foam CNC contour generator
- hot wire CNC foam cutting
- create foam letters from image
- image to vector for foam cutting
- SVG contour for hot wire cutter
- Potrace foam cutter
- raster image to SVG foam cutting
- foam cutter without CAD
- foam cutting without CAD CAM
- beginner foam CNC
- CostyCNC foam cutter
- CostyCNC Stroke Foam Cutter

## Source and license

The repository contains the HTML and JavaScript source code for the project.

The included Potrace implementation retains its original licensing information in `potrace.js`. Check the source file and repository license before redistributing modified versions.

---

**From image to contour, then from contour to G-code: a simple workflow for hot-wire foam cutting.**

