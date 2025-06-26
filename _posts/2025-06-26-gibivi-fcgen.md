---
title: "AI-Powered Flowchart Generation"
date: 2025-06-26
categories: [engineering, product development]
tags: [Flowcharts, Process flow, ideas]
layout: single
---

# Introduction
With gibivi.ai's spoken language based flowchart generation tool, you can explore ideas in the convenient format of a flowchart!

visit https://gibivi.ai today to define visualize your ideas in the form of flowcharts.

![alt text](/assets/images/2025-06-26-gibivi-fcgen/image1.png)

# Organizing of artifacts

The tool provides a convenient way to organize requirement specifications under a Product that you are working on. A Product is a collection of artifacts such as requirements, flowcharts, quotations etc.

![alt text](/assets/images/2025-06-26-gibivi-fcgen/image2.png)

# Providing spoken language prompt

Enter the spoken language prompt in the text area and click on Generate Flowchart.

The tool calls LLM API, parses the response and converts the response into Schemdraw (open source pythong library by Collin J Delker) code to plot the flowchart.

![alt text](/assets/images/2025-06-26-gibivi-fcgen/image3.png)

Naigating across the flowchart is possible with the help of vertical scroll bar and horizontal scroll keys.

# Editing the Flowchart

The schemdraw code can be viewed and edited by clicking on the View Source Code button

![alt text](/assets/images/2025-06-26-gibivi-fcgen/image4.png)

Refer below documentation to understand and learn Schemdraw code:

https://schemdraw.readthedocs.io/en/stable/elements/flow.html

https://schemdraw.readthedocs.io/en/stable/usage/placement.html#connecting-elements

# Exporting and Download

The flowchart can be exported and downloaded in SVG image format.

# Accessing the past prompts

The past prompts can be accessed from the left side drawer. From here, the prompt can be renamed, assigned to a product or can be completely deleted.

![alt text](/assets/images/2025-06-26-gibivi-fcgen/image5.png)

# Thank you for your time!

Please email your feedback to yogesh@gibivi.ai
