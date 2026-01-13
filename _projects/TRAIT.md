---
layout: page
title: TRAIT
description: A <b>TR</b>usted Medi<b>A</b> D<b>I</b>s<b>T</b>ribution Framework
main_title: <h1 align=center>TRAIT - A <b>TR</b>usted Medi<b>A</b> D<b>I</b>s<b>T</b>ribution Framework</h1><hr>
main_description: <h2 align=center>Building Trust in Digital Media</h2>
img: assets/img/TRAIT/kodim23.png
importance: 3
category: PostDoc
---

<style>
h2   {
     color: #429435;
     font-size:180%;
     }
</style>

---

In today’s world, seeing is no longer believing.
With deepfakes and advanced AI image editing, anyone can create highly realistic fake media, and public trust in digital content is eroding fast.


<!--#<br>## Goal-->

Our goal with TRAIT was simple but ambitious:
to make digital media trustworthy again by ensuring integrity, authenticity, and provenance from creation to consumption.

TRAIT is a framework for trusted media distribution that combines:

- **A universal metadata schema:** built in XML and implemented using the Extensible Metadata Platform(XMP), so it can embed directly into any media file.

- **A blockchain core:** using Hyperledger Fabric to record ownership, copyright, and modification history.

- **AI-powered manipulation detection:** integrating modern image forensics algorithms (like MVSS-Net) to flag tampering.

- **Distributed storage:** via IPFS, ensuring transparency and decentralisation.

Think of TRAIT as a digital “chain of custody” for media files, every edit, owner, and verification is securely logged and traceable.

*Based on the paper TRAIT: A Trusted Media Distribution Framework {%cite rainey2023trait %}*

<br>
## How It Works
---
<br>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TRAIT/Framework_v6.png" title="TRAIT Framework." class="img-fluid rounded" %}
    </div>
</div>
<br>
- **Registration -**
A creator uploads an image through the TRAIT web interface.
A unique ID is generated, metadata and a watermark are embedded, and the record is added to the blockchain.

- **Verification -**
When another user uploads or searches for an image, TRAIT compares it to existing records.
If the image has been altered, the manipulation engine highlights what changed and when.

- **Authentication -**
TRAIT uses two types of authentication. The first is **blind passive authentication**, which applies techniques like MVSS-Net to spot any signs of tampering. The second is a **self-embedded watermark** approach, which can rebuild the original image using information stored in its embedded metadata.

- **Information Retrieval -**
All verified versions are stored on IPFS, with transparent transaction history available to anyone.

<div style="padding-left:10%; padding-right:10%; width:100%;">
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TRAIT/ImageReconExample.png" title="Example of Image Reconstruction." class="img-fluid rounded" %}
    </div>
</div>
</div>
<div class="caption">
Image Reconstruction Example.
</div>




<br>
## Real-World Use Cases
---
**Protecting Photographers:**

A photographer registers their original image on TRAIT.
When someone tries to upload an edited version, the system detects the manipulation, flags copyright infringement, and stops false registration.

**Authenticating Artwork:**

An art collector uses TRAIT to verify that a painting is genuine.
A digital photo of the piece is compared against the original’s record, revealing whether it’s authentic or a forgery.

<br>

## Why It Matters
---
TRAIT bridges the gap between media creation and trustworthy distribution.
Unlike existing industry efforts such as Adobe’s C2PA, TRAIT not only records provenance, it actively detects tampering and stores data decentrally.

We see TRAIT supporting industries like:

- Digital media and journalism

- Galleries, libraries, archives, and museums (GLAM)

- Insurance and intellectual property management

<br>

## Key Takeaways
---

**Trust can be built into media:**
TRAIT shows that we don’t have to just “hope” content is real, we can actually prove it.

**AI can be used for good:**
Instead of spreading fakes, it can help spot them by detecting subtle manipulations in images and video.

**Blockchain isn’t just about crypto:** In TRAIT, it’s used to track the history of media, making every piece traceable and transparent.

**Everyone benefits:** Creators can prove their work is authentic, and audiences get confidence that what they’re seeing is the real thing.

<br>

## Looking Ahead
---

TRAIT is just the beginning of what trusted media could look like. The next steps are all about taking it beyond the lab and into the real world:

**Integrate with everyday platforms:** from social media to news outlets, so content verification happens automatically in the background.

**Collaborate with creators and industry partners:** to make authenticity tools easy to use, not just powerful.

**Refine the tech:** improving detection accuracy, reducing processing time, and adapting to new forms of AI-generated media.

**Expand to other media types:** including audio and video, so every format of digital content can be trusted.

The vision is simple: a digital world where authenticity is built in, not an afterthought, and TRAIT is the first step in making that possible.
