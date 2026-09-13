# Card visual for social posts

`carte-template.html` renders one Ouch! card as a 1080×1350 image (Facebook / LinkedIn feed) in the victim-side register: yellow background, white card with hard black border and shadow, purple call-to-action band.

Edit the text in the HTML (kicker, emoji, quote with the highlighted concrete element, sector badge, hashtag), then:

```bash
/opt/pw-browsers/chromium-1194/chrome-linux/chrome --headless=new --no-sandbox --disable-gpu \
  --hide-scrollbars --window-size=1080,1350 --screenshot=carte.png "file://$PWD/carte-template.html"
```

Rules carried by the template: statement in the first person with one concrete element highlighted, hashtag names the context (never an entity), no entity name in the visual, the ask is « swipe à droite » + « dépose-la », the link goes in the first comment.
