---
layout: page
title: NEVIS
description: <b>NE</b>uromorphic <b>VI</b>sion <b>S</b>ystem
main_title: <h1 align=center><b>NE</b>uromorphic <b>VI</b>sion <b>S</b>ystem (<b>NEVIS</b>)</h1><hr>
main_description: <h2 align=center>Building Brain-Inspired Vision Systems That See, and Think, Like We Do</h2>
img:  assets/img/NEVIS/28x28-epoch1-6000-reset10.png # assets/img/NEVIS/kria_crop.png
importance: 3
category: PostDoc
related_publications: true
---
<style>
h2   {
     color: #429435;
     font-size:180%;
     }
</style>

---
The human brain remains one of the best vision systems on the planet. It recognises patterns, adapts to change, and knows instantly when something looks “off.” Modern AI vision systems, on the other hand, often stumble over these things. They’re powerful, but also rigid, power-hungry, and not great at admitting when they’re wrong.

That contrast inspired our recent research, presented in two papers at **SPIE 2024** Conferences:

1. _“Digit Classification using Biologically Plausible Neuromorphic Vision”_ {% cite  maier2024digit %} where we taught a spiking neural network to see digits like the brain does, and

2. _“An FPGA-based Neuromorphic Vision System Accelerator”_ {% cite ali2024fpga %} where we brought that idea to life on real, low-power hardware.


Together, they show how we can make machines that don’t just _see_ like us, but also _think_ more like us.

<br>
<h2> Seeing the World in Edges, Not Pixels</h2>
---

In our first paper, we focused on how to give an AI vision model a more **biological way of seeing**. The human visual cortex doesn’t start with whole objects, it starts with edges and orientations. Neurons in the brain fire for horizontal or vertical lines, and higher layers gradually assemble those into shapes and objects.

We applied the same logic to a **spiking neural network (SNN)** trained on the **MNIST** handwritten digits dataset. Before the network even began learning, each image passed through simple **Prewitt filters** that extract edges. Instead of raw brightness values, the SNN saw lines and contours, the same way your brain does.

This approach made the network’s learning more stable and interpretable. And when we added a twist, resetting about 10% of its neurons back to an untrained state after learning, something interesting happened. Those “untrained” neurons acted like **error detectors**, firing only when the input didn’t belong to any known category. Suddenly, our system wasn’t just classifying digits, it could tell when something _wasn’t_ a digit at all.

On tests with random images from the CIFAR-100 dataset, the edge-based, partially untrained model rejected over **96%** of non-digit inputs correctly, compared to near-zero for the pixel-based version. It became a system that knew what it knew, and what it didn’t.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NEVIS/28x28-epoch1-1000.png" title="1000 Epochs" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NEVIS/28x28-epoch1-3000.png" title="3000 Epochs" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NEVIS/28x28-epoch1-6000-reset10.png" title="6000 epochs, 10 neurons reset" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
100 neurons trained for 1000 images (left) and 3000 images (centre), and trained on 6000 images with 10 neurons weights reset to random values (right).
</div>


<br>
<h2> Bringing the Brain to Hardware</h2>
---

Of course, building a clever algorithm is one thing. Running it efficiently in the real world is another.

In the second paper, we took our neuromorphic vision model and built it on a **Xilinx Kria KV260 FPGA**, creating what we call **NEVIS (NEuromorphic VIsion System)**. The goal: make the system not only _biologically plausible_ but also _practically efficient._

FPGAs (Field-Programmable Gate Arrays) are reconfigurable chips that can perform thousands of operations in parallel, perfect for simulating spiking neurons that all fire at once.
The pipeline developed for the FPGA is shown below:
<div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NEVIS/SNNFPGA.png" title="FPGA SNN Pipeline." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
FPGA SNN Pipeline.
</div>
On the FPGA, NEVIS processed images about **40× faster** and used **less power** than a standard **Raspberry Pi 4B**, even though the Pi’s CPU runs at a much higher clock speed.

<div style="padding-left:25%; padding-right:25%;">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NEVIS/kria.jpg" title="kria FPGA" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Xilinx Kria KV260 FPGA.
</div>
<br>
Here’s how it stacked up:

<div align=center markdown=1>

|Platform|Inference Time|Power Use|Speed Gain|
|---|---|---|---|
|Raspberry Pi 4B|1,550 ms|6.4 W|—|
|Xilinx Kria KV260 FPGA|38 ms|3.8 W|**≈ 40× faster**|

</div>
<br>
That speed-up comes from the FPGA’s natural parallelism, every neuron and synapse can compute simultaneously, just like a biological brain.

<br>
<h2>Why This Matters</h2>
---

Taken together, these two studies show how **neuromorphic computing** can lead to systems that are not only faster and more efficient but also more _aware_ of what they’re seeing.

By combining biologically inspired learning with energy-efficient hardware, we’re getting closer to vision systems that could power small, autonomous devices: drones that navigate intuitively, cameras that understand context, or wearables that interpret their surroundings in real time.

In short, this is a step toward machines that see with structure, think with spikes, and know their own limits, a more human kind of intelligence, built from silicon and science.

<br>

<h2>Key Takeaways</h2>
---
- **Brains do it better, and smarter.** By mimicking how the visual cortex processes edges and patterns, neuromorphic vision systems can learn more efficiently and handle unfamiliar data with greater robustness.

- **Untrained neurons can be useful.** Resetting a small portion of neurons after training helped the model recognise when it was seeing something new, adding a sense of “uncertainty awareness” that most AI systems lack.

- **Edge-based preprocessing improves stability.** Feeding the network structured, edge-detected inputs (instead of raw pixels) led to smoother learning and better generalisation.

- **Hardware matters.** Running the same model on an FPGA delivered ~40× faster performance and better energy efficiency than a Raspberry Pi 4B, proving that brain-inspired AI can be practical on small, low-power devices.

- **Towards smarter, humbler AI.** Combining biologically inspired algorithms with efficient hardware is a promising path toward AI that can not only see but also understand its own limits, much like the human brain.

<br>

<h2> Looking Ahead </h2>
---

The next challenge is to go beyond simple edge detection and digits. The human visual system processes hundreds of orientations, textures, and motion cues across many layers. Expanding NEVIS to capture that richness, and doing so efficiently on hardware, is the natural way to progress.

The more we learn from the brain, the closer we get to building machines that not only _see_ the world but truly _understand_ it.
<br>
<br>
