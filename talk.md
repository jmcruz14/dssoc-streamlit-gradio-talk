---
marp: true
footer: 'This slide was created in MARP, short for Markdown Presentation Ecosystem.'
---
# Streamlit / Gradio
by Jay Cruz, UP Data Science Society

---
# Streamlit/Gradio
by Jay Cruz, UP Data Science Society
![bg right](/Users/jay/Desktop/misc-repos/dssoc-streamlit-gradio-talk/talk/funny_images/cruz_juan_carlos.jpg)

---
# Streamlit/Gradio: Python in a web dev costume
<sup>Web development for Python addicts :> </sup>

####

by Jay Cruz, UP Data Science Society
![bg right](/Users/jay/Desktop/misc-repos/dssoc-streamlit-gradio-talk/talk/funny_images/cruz_juan_carlos.jpg)

---
<!-- header: 'Streamlit/Gradio: Python in a web dev costume' -->

# Expectations
*You probably have some awareness of the following:*
- Python as a programming language (basic syntax, features)
- Data Science & Analytics (charts, statistical models, etc.)
- Other pertinent dev practices (DevOps, GitHub, Git, etc.)

__If you aren't at least familiar with the first two (beginner-level at least), this talk may be too fast for you to keep up. But we're livestreaming this so you can revisit it later.__

---

# What this talk is not about
- How to implement full-fledged models sourced from the cloud
- How to code in Python / JS
- How to test your application
- How to write in MARP
- 1 + 1 = 2

---


---

# Outline
1. My personal background
2. Why Streamlit/Gradio matter?
3. Live demo
4. Why Streamlit/Gradio shouldn't matter?
5. Other tips
---
<!-- <style>
  .container {
    display: flex;
    width: 100%;
  }
  .col {
    flex: 1
  }
</style> -->

# My personal background
- Graduated in 2022
- Took up some subjects in Data Science & Analytics during my college days
- Worked half a year for UP, then 8 months at a startup
- Currently splitting time between volunteer work at Omdena and other side businesses where I try to apply my Data Science & Analytics skills

> *If I were to describe my career in a word, it would be curiosity.*
- I dabbled in two popular languages (JS, Python), studied another one briefly (Go)
- Software dev experiences somehow convinced me to shift from pursuing a DS role to go into DE

<!-- <div class="container">
  <div class="col">
    test
  </div>
  <div class="col">
    test
  </div>
</div> -->

<!--  -->

---

### A little caveat about everything in this talk...
- <u>Sometimes, I feel undeserving of being a part of the org's Education and Research Team</u>
- Outside of volunteer work, barely anything to consider as a professional career in data
- Team thinks my knowledge is still relevant enough to share to the community and I appreciate it!
- *imposter syndrome is real... but if you guys learn something from my talk regardless then i guess i have inspired you!*
- **Feel free to tell me in the comments/chat if there are any errors/incorrect usage/terminologies. I'm not an expert in everything!**

---
<style>
  .container {
    display: flex;
    width: 100%;
  }
  .col {
    flex: 1
  }
</style>

# Why Streamlit / Gradio

<div class="container">
  <div class="col">
    <img src="https://streamlit.io/images/brand/streamlit-logo-primary-colormark-darktext.png" />
  </div>
  <div class="col">
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQdC1xNkDaMNEbtQRyupw5v32HSGVA6w0zNjA&s" />
  </div>
</div>

---
<!-- header: 'Streamlit/Gradio: Python in a web dev costume - Why Streamlit/Gradio?' -->

### Life before Streamlit
- Flask & Django
- Dash Plotly and other wrappers*

---

#### Flask and Django
![width:200px](https://upload.wikimedia.org/wikipedia/commons/3/3c/Flask_logo.svg)
![width:200px](https://www.fullstackpython.com/img/logos/django.png)

---

![bg right width:600px](https://blog.jetbrains.com/wp-content/uploads/2023/11/django-vs-flask-restful.png)


#### Flask & Django
- Web frameworks
  - *framework* - "underlying system, concept or text"
  - Nuanced to web - <u>A standard way of building applications</u> (most often, these **standards are designed/built by other people so you don't have to**)
- *Building in Python to be deployed over the web*

---

#### Flask & Django
- In terms of use cases, people may often choose to build straight within Flask/Django (front-end and back-end are enclosed in the same script) OR they use Flask/Django separately
- Personally, I've worked in a personal project that uses **FastAPI** (the other web framework that seems much, much cooler imo)

---

![bg right width:400px](https://www.greghilston.com/post/how-to-use-plotly-plotly-express-and-dash-with-jupyterlab/featured-image.png)

#### Dash Plotly, and other wrappers
- *wrapper* - "something that encapsulates/obfuscates other components"
  - Dash Plotly is built on top of Flask (very friendly too with regards to making dashboards)
  - **This is also how I built my first application as a school requirement**

---

```Python
import dash
import dash_bootstrap_components as dbc
import dash_core_components as dcc
import dash_html_components as html
import dash_table
import pandas as pd

from dash.exceptions import PreventUpdate

navbar = dbc.Navbar(
    [
        dbc.Row(
            [
                html.Img(
                    src=app.get_asset_url('companylogo.jpg'), 
                    style={'height':'5%', 'width':'5%', 'padding-Right': '10em'}
                    ),
                    html.A(
                    dbc.NavbarBrand(
                        "Pet Shelter", 
                        style={'padding':'10px', 'margin-Left':'10em','font-family':'Avenir'}, 
                        className="m1-2"),
                        href="/home",
                        style = {'padding-Left': '5px'}
                        )
            ],
            align='center',
            no_gutters=True,    
        )

    ],
    dark = True,
    color = '#ffaa00'
)

```

---

#### Flask & Django
- Consider the following steps after a person has completed coding their application: 

<img style="width:75%" src="/Users/jay/Desktop/misc-repos/dssoc-streamlit-gradio-talk/talk/funny_images/flowchart_old_days.png" />

---

# In terms of time-to-deployment, this may get really, really long.
(Not even accounting for the debugging time, bugs, etc.)

---

<img style="width:75%" src="/Users/jay/Desktop/misc-repos/dssoc-streamlit-gradio-talk/talk/funny_images/flowchart_with_highlight.png" />

This is what **Streamlit and Gradio** try to do: **simplify and make this section of deployment easier**. 

---

<div class="container">
  <div class="col">
    <img src="https://streamlit.io/images/brand/streamlit-logo-primary-colormark-darktext.png" />
  </div>
  <div class="col">
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQdC1xNkDaMNEbtQRyupw5v32HSGVA6w0zNjA&s" />
  </div>
</div>

- An "open-source Python library that makes it easy to create and share custom web apps for machine learning and data science" (Streamlit, according to the [Snowflake](https://docs.snowflake.com/en/developer-guide/streamlit/about-streamlit) docs)
- Has their own simplified hosting services (All you need is to click Deploy!)
- **Much, much more simplified coding** (more on this in the next slide)
- Has support for packages/libraries that are relevant to the field of Data Science and Analytics
- **A low-code alternative to developing web applications**

---
<style>
  .container {
    display: flex;
    width: 100%;
    gap: 1em
  }
  .col {
    flex: 1
  }
</style>

## Building web components and elements

<div class="container">
  <div class="col">

##### Regular HTML & CSS
```HTML
<style>
  .container {
    display: flex;
    width: 100%;
    margin: 1em;
  }
</style>

<div class="container">
  Hello world!
</div>
```

  </div>

  <div class="col">

##### Flask/Django

```HTML
<style>
    .container {
        display: flex;
        width: 100%;
        margin: 1em;
    }
</style>
<div class="container">
    {{ content }}
</div>
```

```Python
from flask import render_template
@app.route('/')
def home():
    return render_template('template.html', content='Hello world!')
```
  </div>

</div>

---

##### Streamlit
```Python
import streamlit as st

with st.container():
  st.write("Hello world!")
```

##### Gradio
```Python
import gradio as gr

with gr.Blocks() as demo:
  with gr.Row():  # This creates a container-like element
        gr.Markdown("Hello world!")
```

- A lot of the complications in older Python web frameworks are dealt away
- Rendering web pages, elements, etc. are made much, much easier in Streamlit

---
<!-- header: 'Streamlit/gradio: Python in a web dev costume - Live demo' -->

# Live Demo

### Objectives
- Build a simple 2-page dashboard application displaying data 
- Demonstrate functionality, visual display, and deployment of application
(build a simple dashboard application using dummy data, target is to show the ff)
(functioning charts, functioning buttons, with a select button)

---

### Things to prepare for
- 

---

# Why NOT streamlit / gradio?
<sup>The part where I kind of rant about the two frameworks as a whole.</sup>

---
<!-- header: 'Why NOT streamlit/gradio?' -->

#### Low-code tools
- Things are abstracted
  - Abstraction in a component tends to mean it is more difficult to tweak if there are certain needs that aren't met
  - Important to emphasize as when certain processes are black boxed, you might not get the chance to fix the styling / design / functionality of things correctly



---

### Cons
- Limited customization
- Sometimes gets hard to debug because of the low-code set-up
- May be a crutch (<u>It is still an advantage for anyone to get into web development. Especially people here who will be doing visualization tasks.</u>)

---

### MARP!
Markdown Presentation Ecosystem

## Sometimes, PowerPoint just does things better. You don't like this type of simplicity? You need more intricate design patterns, image placements, etc, just go for PowerPoint. 

---
<!-- header: '' -->

## Links
- [Github Link]() / jmcruz14
- [LinkedIn]() / Juan Carlos Cruz

## Contact Me
*Email: jcmcruz14@gmail.com*
*You may also reach out to me via LinkedIn.*
*If you are a UP undergraduate/alumni, you may also reach me by joining the UP Data Science Society. I try to be active every semester and give back to people.*