---
title: 'My Khan Academy trig functions test'
date: 2022-07-04T17:30:00+02:00
draft: false
tags: [trigonometry, khan academy, math]
---

After months of hard work, finally I have 100% in the Khan Academy Trigonometry section. This was my last exam, which I had to take it several times before reaching the ace!

<div class="align-stuff">
<img style="margin:0; max-height:100vh" src="/joji_fx/images/post04/unit-test-trig-0.jpg" alt="A funny kid with a giant bubble gum on his mouth]">
<img style="margin:0; max-height:100vh" src="/joji_fx/images/post04/unit-test-trig-1.jpg" alt="A funny kid with a giant bubble gum on his mouth]">
</div>

With my new acquired knowledge, let’s try to code a canvas animation which will show the relationship between the unit circle and a the graph of a sinusoidal function.

I would like to do something like this:

<div class="align-stuff">
<a title="Lucas Vieira, Public domain, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Circle_cos_sin.gif"><img width="512" alt="Circle cos sin" src="https://upload.wikimedia.org/wikipedia/commons/3/3b/Circle_cos_sin.gif"></a>
</div>

<div class="align-stuff">
EDIT 09/07/22
</div>

### First try:

<script src="https://gist.github.com/mugiwarafx/7e765db443837f520daef80dc9ffdebc.js"></script>

#### First try result:

<div class="align-stuff">
<img style="margin:0; max-height:100vh" src="/joji_fx/images/post04/first-try.gif" alt="A sinusoidal function graph animated">
</div>

As you can see I am not even close 😅, but it was fun to do it! 😎

#### First try References:

[MDN web docs\_/References/Web APIs/Canvas API/Canvas tutorial/Basic animations](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations)

[@gkhays gist: Oscillating sine wave, including the steps to figuring out how to plot a sine wave](https://gist.github.com/gkhays/e264009c0832c73d5345847e673a64ab)

<div class="align-stuff">
EDIT 10/07/22
</div>

### Second try:

<script src="https://gist.github.com/mugiwarafx/7dc3fc10d6687def23c00fed256f8c1c.js"></script>

#### Second try result:

<div class="align-stuff">
<img style="margin:0; max-height:100vh" src="/joji_fx/images/post04/second-try.gif" alt="A sinusoidal function graph animated">
</div>

That was close! Okay I am kidding. Actually this one is better than the first try, as you can see, but is still far from the desired result. There are several TODOs that must be done to reach the true power of the light side of the force. So hopefully, I will come in the near future with a JEDi solution. Meanwhile, just chill a lil bit watching sinus waves 🦄

#### Second try References:

[TW @code_laboratory HTML Canvas Tutorial](https://www.youtube.com/watch?v=uCH1ta5OUHw&t=2406s)

[HTML spec about canvas element](https://html.spec.whatwg.org/multipage/canvas.html)

### Next try TODOs:

- turn the animation into a real sinx function
- match the freq with unit circle angle (right now this is hardcoded)
- update this post with the result
- feed the cat! 0 9 \* \* \*
