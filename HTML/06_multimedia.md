# 🟠 Level 6 — HTML Multimedia ⭐⭐

Now we move into **multimedia and embedded content** in HTML.

This level is smaller than Forms, but it is important because modern websites commonly use:

* Videos
* Audio
* Captions/subtitles
* YouTube videos
* Podcasts
* Tutorials
* Product videos
* Background/hero videos

The main elements are:

```text
<audio>
<video>
<source>
<track>
<iframe>
```

And you should understand:

```text
controls
autoplay
muted
loop
poster
captions/subtitles
```

---

# 73. `<audio>`

The `<audio>` element is used to embed audio content.

Basic example:

```html
<audio controls src="song.mp3"></audio>
```

The browser provides audio controls.

Conceptually:

```text
┌────────────────────────────────────┐
│ ▶ ━━━━━━━●━━━━━━━━  🔊             │
└────────────────────────────────────┘
```

---

## Better approach: `<source>`

Instead of putting `src` directly on `<audio>`, you can use `<source>`:

```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
</audio>
```

This becomes particularly useful when you have multiple formats.

```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    <source src="song.ogg" type="audio/ogg">

    Your browser does not support audio.
</audio>
```

The browser can choose a supported source.

---

# 74. `<video>`

`<video>` embeds video content.

Basic example:

```html
<video controls src="movie.mp4"></video>
```

More commonly:

```html
<video controls width="640">
    <source src="movie.mp4" type="video/mp4">
</video>
```

You can also provide fallback text:

```html
<video controls width="640">
    <source src="movie.mp4" type="video/mp4">

    Your browser does not support the video element.
</video>
```

---

# ⭐ Video vs Audio

| `<audio>`        | `<video>`              |
| ---------------- | ---------------------- |
| Audio only       | Video + audio          |
| Music            | Movies                 |
| Podcasts         | Tutorials              |
| Voice recordings | Product demonstrations |
| Audio books      | Training videos        |

---

# 75. `<source>`

`<source>` specifies a media source for `<audio>` or `<video>`.

Example:

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
</video>
```

You can provide multiple sources:

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
</video>
```

The browser selects an appropriate source it can play.

---

## Why multiple formats?

Different browsers/platforms may have different media format/codec support.

For example:

```html
<video controls>
    <source src="video.webm" type="video/webm">
    <source src="video.mp4" type="video/mp4">
</video>
```

The browser can try the available sources in order.

---

## `type` attribute

```html
<source
    src="video.mp4"
    type="video/mp4"
>
```

The `type` tells the browser what kind of media the source represents.

Audio:

```html
<source
    src="song.mp3"
    type="audio/mpeg"
>
```

Video:

```html
<source
    src="movie.mp4"
    type="video/mp4"
>
```

---

# 76. `<track>`

`<track>` provides timed text associated with video/audio, most commonly:

* Captions
* Subtitles
* Descriptions
* Chapter information

Example:

```html
<video controls>
    <source src="lesson.mp4" type="video/mp4">

    <track
        src="captions.vtt"
        kind="captions"
        srclang="en"
        label="English"
    >
</video>
```

This is very important for accessibility.

---

# ⭐ What is `.vtt`?

`<track>` commonly uses **WebVTT** files.

Example:

```html
<track
    src="captions.vtt"
    kind="captions"
    srclang="en"
    label="English"
>
```

The `.vtt` file contains timed text.

Conceptually:

```text
00:00:01.000 --> 00:00:04.000

Welcome to this HTML tutorial.
```

The browser synchronizes the text with the video.

---

# `kind`

The `kind` attribute tells the browser what type of track it is.

Common values include:

```text
captions
subtitles
descriptions
chapters
metadata
```

For example:

```html
<track
    src="english.vtt"
    kind="subtitles"
    srclang="en"
    label="English"
>
```

or:

```html
<track
    src="captions.vtt"
    kind="captions"
    srclang="en"
    label="English"
>
```

---

# `srclang`

Specifies the language of the track.

```html
srclang="en"
```

means English.

Examples:

```html
srclang="hi"
```

Hindi.

```html
srclang="fr"
```

French.

```html
srclang="de"
```

German.

---

# `label`

Provides a human-readable name for the track.

```html
label="English"
```

Another:

```html
label="Hindi"
```

---

# `default`

You may also see:

```html
<track
    src="english.vtt"
    kind="captions"
    srclang="en"
    label="English"
    default
>
```

`default` indicates that this track should be the default track when appropriate.

---

# 77. `<iframe>`

`<iframe>` means **inline frame**.

It allows another document/resource to be embedded inside your webpage.

Example:

```html
<iframe
    src="https://example.com"
    width="600"
    height="400"
>
</iframe>
```

Conceptually:

```text
┌────────────────────────────────────┐
│             YOUR PAGE              │
│                                    │
│   ┌────────────────────────────┐   │
│   │       EMBEDDED PAGE        │   │
│   │                            │   │
│   │       iframe content       │   │
│   │                            │   │
│   └────────────────────────────┘   │
│                                    │
└────────────────────────────────────┘
```

---

# Common Uses of `<iframe>`

### YouTube videos

A video platform can provide an iframe embed.

Conceptually:

```html
<iframe
    src="https://www.youtube.com/embed/VIDEO_ID"
    title="HTML Tutorial"
    width="560"
    height="315"
    allowfullscreen
></iframe>
```

### Google Maps

Maps can be embedded using an iframe.

### External documents

Some services provide iframe-based embeds.

### Payment/authentication widgets

Some third-party systems can also use embedded frames, depending on their architecture.

---

# ⭐ Important `<iframe>` Interview Concept

An iframe creates a **separate browsing context**.

Think:

```text
Your webpage
     │
     └── iframe
           │
           └── separate document
```

The embedded document is not simply equivalent to copying its HTML into your page.

Security rules such as the **same-origin policy** affect how the parent page and iframe can interact.

---

# `title` on iframe

For accessibility, give meaningful iframes a `title`.

Good:

```html
<iframe
    src="..."
    title="Company location map"
></iframe>
```

Better than:

```html
<iframe src="..."></iframe>
```

The title tells assistive technologies what the embedded content represents.

---

# 78. Video/Audio `controls`

The `controls` attribute tells the browser to display built-in media controls.

```html
<video controls>
    <source src="movie.mp4" type="video/mp4">
</video>
```

Without:

```html
<video>
    <source src="movie.mp4" type="video/mp4">
</video>
```

the browser doesn't automatically have to display the standard user controls.

With:

```html
controls
```

the user can typically access things such as:

* Play/pause
* Volume
* Seeking
* Fullscreen for video
* Other browser-provided controls

---

# Boolean Attributes

Notice:

```html
<video controls>
```

There is no:

```html
controls="true"
```

`controls` is a **boolean attribute**.

Its presence means enabled.

Similarly:

```html
<video muted>
```

means muted.

```html
<video autoplay>
```

means autoplay is requested.

---

# 79. `autoplay`

`autoplay` asks the browser to start media automatically.

```html
<video autoplay>
    <source src="video.mp4" type="video/mp4">
</video>
```

However, modern browsers often restrict **autoplay with sound**.

This is why you commonly see:

```html
<video autoplay muted>
```

The browser is much more likely to allow autoplay when the media is muted.

---

# ⭐ Autoplay + Muted

Common background-video pattern:

```html
<video
    autoplay
    muted
    loop
>
    <source src="background.mp4" type="video/mp4">
</video>
```

The idea is:

```text
autoplay → start automatically
muted    → no sound
loop     → repeat continuously
```

---

# 🚨 Important Interview Point

Don't say:

> "`autoplay` always makes a video play automatically."

More accurate:

> `autoplay` requests automatic playback, but browser autoplay policies can prevent playback, particularly when media has audible sound.

---

# 80. `muted`

`muted` starts media without audio.

```html
<video
    autoplay
    muted
>
    <source src="background.mp4" type="video/mp4">
</video>
```

Common use:

* Hero/background videos
* Decorative motion
* Silent previews

---

# Why `muted` is commonly paired with `autoplay`

Because browsers commonly restrict automatic playback of media with audible sound.

So you'll frequently see:

```html
<video autoplay muted>
```

rather than:

```html
<video autoplay>
```

---

# 81. `poster`

`poster` specifies an image shown **before the video starts playing**.

Example:

```html
<video
    controls
    poster="thumbnail.jpg"
>
    <source src="movie.mp4" type="video/mp4">
</video>
```

Conceptually:

```text
Before playing:

┌─────────────────────────────┐
│                             │
│       thumbnail.jpg         │
│                             │
│             ▶               │
│                             │
└─────────────────────────────┘
```

Once the video plays, the poster is no longer the displayed video frame.

---

# Why use `poster`?

It improves:

* Visual presentation
* User experience
* Video preview
* Perceived polish

For example:

```html
<video
    controls
    poster="html-course-thumbnail.jpg"
>
    <source src="html-course.mp4" type="video/mp4">
</video>
```

---

# `poster` vs `<img>`

Don't confuse:

```html
poster="thumbnail.jpg"
```

with:

```html
<img src="thumbnail.jpg">
```

`poster` belongs to `<video>` and represents the video's preview image.

---

# 82. Captions / Subtitles ⭐⭐⭐

This is especially important for **accessibility**.

Captions/subtitles allow users to understand spoken or relevant audio content through text.

Example:

```html
<video controls>

    <source
        src="lesson.mp4"
        type="video/mp4"
    >

    <track
        src="english.vtt"
        kind="captions"
        srclang="en"
        label="English"
    >

</video>
```

---

# Captions vs Subtitles

These terms are often used interchangeably, but there's a useful distinction.

### Subtitles

Usually provide the spoken dialogue, often for people who can hear the audio but don't understand the language.

Example:

```text
Speaker:
"Welcome to the HTML course."
```

### Captions

Typically include dialogue **plus relevant audio information**.

For example:

```text
[Music playing]

John:
Welcome to the HTML course.

[Door closes]
```

Captions are particularly useful for people who are deaf or hard of hearing.

---

# ⭐ Why Captions Matter

Captions improve:

* Accessibility
* Comprehension
* Multilingual support
* Viewing in noisy environments
* Viewing without sound

For example, someone watching a tutorial on a train may have their phone muted.

Captions still allow them to follow along.

---

# ⭐ Complete Multimedia Example

Let's combine everything:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>Multimedia Example</title>
</head>

<body>

    <h1>HTML Multimedia</h1>


    <h2>Audio</h2>

    <audio controls>
        <source
            src="podcast.mp3"
            type="audio/mpeg"
        >

        <source
            src="podcast.ogg"
            type="audio/ogg"
        >

        Your browser does not support audio.
    </audio>


    <h2>Video</h2>

    <video
        controls
        width="640"
        poster="thumbnail.jpg"
    >

        <source
            src="lesson.mp4"
            type="video/mp4"
        >

        <source
            src="lesson.webm"
            type="video/webm"
        >

        <track
            src="english.vtt"
            kind="captions"
            srclang="en"
            label="English"
            default
        >

        Your browser does not support video.

    </video>


    <h2>Embedded Content</h2>

    <iframe
        src="https://example.com"
        title="Example website"
        width="600"
        height="400"
    >
    </iframe>

</body>

</html>
```

This example demonstrates nearly everything in Level 6.

---

# ⭐ Background Video Example

You may encounter this in modern landing pages:

```html
<video
    autoplay
    muted
    loop
    playsinline
>

    <source
        src="background.mp4"
        type="video/mp4"
    >

</video>
```

Let's understand:

```text
autoplay
   ↓
Try to start automatically

muted
   ↓
No audio

loop
   ↓
Repeat

playsinline
   ↓
Useful for inline playback on mobile devices
```

`playsinline` wasn't in your list, but **learn it** because it frequently appears with mobile/background videos.

---

# ⭐ Important Media Attributes

Here's your interview cheat sheet:

| Attribute     | Purpose                                   |
| ------------- | ----------------------------------------- |
| `controls`    | Show browser media controls               |
| `autoplay`    | Request automatic playback                |
| `muted`       | Start without audio                       |
| `loop`        | Repeat media                              |
| `poster`      | Preview image for video                   |
| `preload`     | Hint about how media should be preloaded  |
| `width`       | Video display width                       |
| `height`      | Video display height                      |
| `playsinline` | Encourage inline video playback on mobile |

---

# ⭐ `preload` — Bonus Interview Topic

You may see:

```html
<video preload="metadata">
```

Possible values include:

```text
none
metadata
auto
```

Conceptually:

### `none`

Don't preload the media unnecessarily.

```html
<video preload="none">
```

### `metadata`

Load metadata such as duration/dimensions when appropriate.

```html
<video preload="metadata">
```

### `auto`

Allows the browser to preload more of the media.

```html
<video preload="auto">
```

Remember:

> `preload` is a **hint** to the browser, not an absolute command.

---

# ⭐ `<audio>` Complete Example

```html
<audio controls>

    <source
        src="music.mp3"
        type="audio/mpeg"
    >

    <source
        src="music.ogg"
        type="audio/ogg"
    >

    Your browser does not support audio.

</audio>
```

Structure:

```text
<audio>
    │
    ├── <source>
    │
    ├── <source>
    │
    └── fallback text
```

---

# ⭐ `<video>` Complete Example

```html
<video
    controls
    width="800"
    poster="preview.jpg"
>

    <source
        src="course.mp4"
        type="video/mp4"
    >

    <source
        src="course.webm"
        type="video/webm"
    >

    <track
        src="english.vtt"
        kind="captions"
        srclang="en"
        label="English"
        default
    >

    Your browser does not support video.

</video>
```

Structure:

```text
<video>
   │
   ├── <source>
   ├── <source>
   ├── <track>
   │
   └── fallback text
```

---

# 🚨 Common Interview Traps

## 1. `<source>` doesn't play media itself

This:

```html
<source src="video.mp4">
```

is not a standalone video player.

It's used inside media elements such as:

```html
<video>
```

or:

```html
<audio>
```

---

## 2. `<track>` isn't the video

`<track>` provides timed text/data associated with media.

```text
video
  +
track
  ↓
video + captions/subtitles
```

---

## 3. `poster` isn't a permanent image

It is displayed as the video's preview image before playback.

---

## 4. `autoplay` doesn't guarantee playback

Browser policies can block autoplay, especially audible autoplay.

---

## 5. `muted` doesn't mean "remove audio from the file"

It means the media is played without audible audio output.

---

## 6. `controls` doesn't create the media

It only asks the browser to display user controls.

---

## 7. `<iframe>` isn't only for YouTube

It can embed various external documents/resources, depending on whether the target permits framing.

---

# ⭐ Security: `<iframe>`

For iframes, you'll eventually encounter:

```html
sandbox
```

For example:

```html
<iframe
    src="..."
    title="Embedded content"
    sandbox
></iframe>
```

`sandbox` can restrict capabilities of the embedded document.

You'll study this more deeply later in the **HTML Security** section.

Also, when embedding external content, don't blindly trust arbitrary third-party sources.

---

# 🧠 Level 6 Mental Model

Think about multimedia like this:

```text
                  MULTIMEDIA
                      │
          ┌───────────┴───────────┐
          │                       │
       <audio>                 <video>
          │                       │
          │                 ┌─────┼─────┐
          │                 │     │     │
       <source>          source  track  poster
          │                       │
          │                   captions
          │                   subtitles
          │
          └──────────────┐
                         │
                      <source>
```

And:

```text
<iframe>
   ↓
embedded external document/resource
```

---

# 🎯 Level 6 Interview Questions

You should be able to answer these.

### Basic

1. What is `<audio>`?
2. What is `<video>`?
3. What is `<source>`?
4. What is `<track>`?
5. What is `<iframe>`?
6. What does `controls` do?
7. What does `autoplay` do?
8. What does `muted` do?
9. What does `poster` do?
10. What are captions?

### Intermediate

11. Why use `<source>` instead of directly specifying `src`?
12. Can `<audio>` have multiple `<source>` elements?
13. Can `<video>` have multiple `<source>` elements?
14. What is WebVTT?
15. What does `srclang` mean?
16. What does `kind="captions"` mean?
17. Difference between captions and subtitles?
18. Why is `title` useful on an iframe?
19. What is an iframe?
20. Does `autoplay` always work?

### ⭐ Advanced

21. Why is `autoplay` commonly combined with `muted`?
22. What is the purpose of `poster`?
23. What happens when multiple `<source>` elements are provided?
24. How do you add subtitles to a video?
25. How do you make video content accessible?
26. What is the difference between `<iframe>` and `<video>`?
27. What is `sandbox` on an iframe?
28. What is `playsinline`?
29. What is `preload`?
30. Why shouldn't you assume POST/HTTPS-style security concepts automatically make embedded content safe?

---

# 🏆 Level 6 — Must Remember

For interviews, make these automatic:

```text
<audio>
   ↓
<source>

<video>
   ↓
<source>
<track>
```

```text
<iframe>
   ↓
Embeds another document/resource
```

And:

```text
controls → show media controls

autoplay → request automatic playback

muted → no audible audio

loop → repeat

poster → video preview image

track → captions/subtitles/timed text
```

Most importantly:

> **`<video>` + `<track>` + captions = accessibility**

and:

> **`autoplay` does not guarantee automatic playback because browsers can apply autoplay policies.**

---

## 🎯 Practice Task

Build a small **HTML Video Learning Page** containing:

```text
HTML Video Course
│
├── Introduction
│     └── video
│
├── HTML Forms
│     └── video + English captions
│
├── HTML Tables
│     └── video + captions
│
├── Background music
│     └── audio player
│
└── Reference
      └── embedded resource using iframe
```

Try to build it **without looking at the examples**.
