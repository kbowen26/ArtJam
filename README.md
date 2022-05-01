# ArtJam
ITIS 4440 individual project - inspired re-envisioning of the http://te2.tewi.us/ site's drawing program with modern signature APIs.

![ArtJam Demo Photo](https://raw.githubusercontent.com/kbowen26/ArtJam/main/ArtJam/public/ArtJam_screenshot.png)

## The Proposal - 3/19/22
###Summary
This project will aim to provide a wider array of artistic expression by improving on older iterations of browser drawing applications using more modern advancements.

### Objectives
•	Create an appealing browser application.
•	Provide user control over canvas and tool features.
•	Allow on-site saved images and editing, as well as local save file options.

### Project Background
In 2015, one of my first forays into social art shut down. Tegaki E – a website comprised of an online canvas, a handful of colors, some opacity features, and a wealth of artistic community – allowed users to not only create and post set-size art pieces to their account, but gave comment-sized art canvases for users to comment on said pieces. No text, aside from the login and search features; people came together, created social groups, and drew detailed comics together with just those canvases.

I’d never gotten back into another site like it, though someone else eventually created their own version of the same site to keep the magic alive. I’d always been excited by browser drawing programs, particularly those that let people draw together. When I started at Charlotte and decided, like most Computer Science students, I should plan projects, trying to reconstruct that sort of website was at the forefront of my ideas.

### Artjam
An art jam is a social activity where people paint on their own canvases in a group setting. While the timeline for this project may make including social aspects like user accounts, commenting, and other features better fitted for phase two, the spirit of the project is upheld in its name. In hopes of blending aspects of older browser art apps and standalone applications like Photoshop and Procreate, implementing user-customizable canvas and tools is the primary appeal of this project.

Providing custom canvas sizes avoids the historical dilemma in sites like Sketch.io or Drawpile.net, where the artist either has ideas too big for a tiny canvas or has a small sketch lost in a large void. Providing a tool menu that can be moved to one of four corners in the canvas allows users to adjust to their drawing styles as often as they like.

### Deliverables and Success Parameters
•	Users should be able to customize their canvas size to a maximum of their browser window’s dimensions, and a minimum to be determined, before the user begins drawing.
•	Users should be able to drag and drop the in-canvas tool menu to one of four corners in the canvas.
•	At a predetermined minimum size, the tools menu should be off the canvas in a fixed position for maximum canvas access.
•	Users should be able to color pick via Vue-color and should be able to specify colors via Hexcode or RGB input.
•	Users should be able to select brush minimum and maximum size, experience pressure sensitive lines, and opacity of the brush strokes.
•	Users should be able to save their artwork to a main gallery page on the site, as well as save a local copy of predetermined file types (PNG, JPEG, possibly SVG).
•	Users should be able to select and edit an artwork from the main gallery page.

### Required Resources
**Hosting and Database**
Artjam will need a hosting service for the site itself, as well as a database to hold and retrieve submitted SVG files. As it’s a demo for this project specifically, the actual weight of the SVG files and in-browser performance may be handleable for free or trial services such as Firebase, but purchasing a temporary subscription is within budget and can be personally financed if needed.

**Canvas Program Features**
Most solutions look to be available in VueJS. Pressure-sensitive input, the canvas itself, and associated API needs can be provided by Pressure-Sensitive Signature Drawing’s library and Perfect Freehand. The color-picker can be provided by Vue-color, and the Drag n’ Drop Plugin will let us adjust the tools menu within the canvas space. SaveSvgAsPng is one solution for saving locally, although more filetypes may have similar plugins.

### Works Cited
•	Pressure-Sensitive Signature Drawing’s library: https://www.vuescript.com/pressure-sensitive-signature-drawing/
•	Perfect Freehand: https://github.com/steveruizok/perfect-freehand#options
•	Vue-Color: https://www.npmjs.com/package/vue-color
•	SaveSvgAsPng: https://www.npmjs.com/package/save-svg-as-png
•	Drag n’ Drop Plugin: https://vuejsexamples.com/drag-n-drop-plugin-for-vue-js/

## The Process - 3/19/22 - 5/1/22
### Challenges
**Vue 2 and 3**
Vue 3 was made default on February 7th, 2022, and lacks a lot of compatibility with Vue 2, which my initial references were comprised of. This mixture of versions and my familiarity with VueJS in general (starting this semester and thanks largely to the class for which this program was created!), lead to a wealth of back and forth, trials with failures and success, and some amount of redirect in the goals of the project itself.

While most community help and libraries, such as the ones I chose for my program, were in Vue 2 it proved hard to immediately check changes in syntax across the libraries while working. When problem-solving, it was difficult to find which version was being referenced. I'll discuss this in reference to my program in the next section.

**App Capabilities**
While I'd focused on signature capture technologies to reverse-engineer my drawing application, getting the resources to work in the way that I wanted lead me into finding where *those* creators had sourced their resources: the signature application came from a drawing application, one which addressed some issues I'd run into and created others, should I want to reference solutions from that parent program.

Finding the Vue Canvas Drawing application initially provided some insight into the process compared to the Signature Pad, but the strokes weren't smooth and the pressure function was missing. I pivoted back to Signature Pad, which had a feel much closer to my original vision for a drawing program. It wasn't until attempting to incorporate Vue-Color, which wasn't compatible with the program I'd built, that I discovered some changes Signature Pad had made for convenience.

As not intended for full-scale art, Signature Pad didn't save the stroke history and instead maintained one stroke, effectively adding the newest onto the others on the canvas. That meant that when adjusting stroke color or size, the entirety of the lines were affected. Additionally, the canvas itself didn't know how to handle clearing and canvas resizing without offsetting the drawn lines from where the cursor actually is. Ultimately, in the coding process I prioritized the features that I had achieved and polished those into a running application, with room for future reinvisioning on an extended scale.

## The Final Product - 5/1/22
### Features
•	Pressure-sensitive writing
•	Adjustable and clearable canvas
•	Pen color changes
•	Downloadable image

### Future Scope
•	Pen weight
•	Stroke history
•	Offset fixes
•	User login and profiles
•	On-site saves in addition to downloads
•	User sharing and collaborative canvases

### Reflection
This process was challenging in a very good way. With this and my group project, it's ultimately the closest to fully functioning applications my coursework has given me space for. I had this project in a book, with a few other project ideas, the week I started at UNC Charlotte, and to see some version of it realized the semester I graduate is ridiculously gratifying. I've learned more about pacing and expectation management than anything, and seeing proposals being paired down as the reality of the workload sets in has given me a sorely needed lesson in estimating reasonable scope.

I challenged myself with a language I wasn't entirely comfortable in, struggled to find solutions and adjust my expectations, and have seen a lot of value in being able to work in a team setting on projects like this because of the value of experience in my peers. Thank you for your time, your consideration, and the opportunity to do something like this.
