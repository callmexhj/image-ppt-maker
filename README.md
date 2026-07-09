# image-ppt-maker

Codex skill for creating PPT-style slide images with a review-gated workflow:

- clarify presentation requirements, including optional top-corner LOGO space;
- draft McKinsey-style master and page-by-page outlines;
- confirm visual style before image prompts;
- generate unified image-2 prompts and 16:9 slide images;
- automatically assemble a playable 16:9 HTML slideshow;
- write final oral speaker notes based on the outline and generated images.

## Install

Copy this repository folder into your Codex skills directory:

```powershell
Copy-Item -LiteralPath . -Destination "$env:USERPROFILE\.codex\skills\image-ppt-maker" -Recurse -Force
```

Then invoke the skill with:

```text
$image-ppt-maker
```
