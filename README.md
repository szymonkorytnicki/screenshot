# screenshot

Create screenshot on each Hot Module Reload event and combine them into interactive video.

- Create plugins for Vite, Webpack etc.
- Ability to configure video, quality, speed... etc

PoC for Vite:

```
if (import.meta.hot) {
  import.meta.hot.on("vite:afterUpdate", () => {
    const screenshotTarget = document.body;
    console.log("doing");
    html2canvas(screenshotTarget).then((canvas) => {
      const base64image = canvas.toDataURL("image/png");
      const img = document.createElement("img");
      img.src = base64image;
      document.body.appendChild(img);
    });
  });
}
```
