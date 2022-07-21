# Tools and software

# Dear PyGui resources
- [Showcase](https://github.com/hoffstadt/DearPyGui/wiki/Dear-PyGui-Showcase)
- [Issues](https://github.com/hoffstadt/DearPyGui/issues)
- [Commits](https://github.com/hoffstadt/DearPyGui/commits/master)
- [Stargazers](https://github.com/hoffstadt/DearPyGui/stargazers)
- [Download stats](https://pepy.tech/project/dearpygui)
- [API documentation](https://dearpygui.readthedocs.io/en/latest/index.html)
- [DPG EXT](https://pypi.org/project/dearpygui-ext/)
- [demo.py code](https://github.com/hoffstadt/DearPyGui/blob/master/DearPyGui/dearpygui/demo.py)
- [Examples by Another Alex](https://github.com/yet-another-alex/dearpygui-examples)
- [Examples by Illu](https://github.com/Mstpyt/DPG-Examples)
- [Examples by Preston incl. OpenCV](https://github.com/Pcothren/DearPyGui-Examples)
- [Discord](https://discord.gg/tyE7Gu4)
- [Reddit Python GUI](https://www.reddit.com/search/?q=python%20gui&sort=new)
- [Reddit DearPyGui](https://www.reddit.com/r/DearPyGui/new/)
- [Raccoon Music Player](https://github.com/bandit-masked/raccoon)
- [RMP Reddit](https://www.reddit.com/r/Python/comments/sp7ddv/my_first_project_raccoon_music_player_cute/)
- [Pixl engine](https://github.com/Atlamillias/dearpypixl)

# Apps under development

[Solar tracker](https://github.com/iOsnaaente/Supervisorio_TrackerSolar) | [Searchable tag record](https://github.com/sharkbound/pythontools/tree/master/examples/dearpyguiapps/index_ui) | [ML app](https://github.com/JEENB/Machine-Learning-Using-Socket-Programming)  | [Ultime IOC Engine](https://github.com/SilverPlate3/Ultimate_IOC_Engine/issues/1) |  [Colorization](https://github.com/168762321/colorization/issues/19) | [Drag and drop Project mgt](https://github.com/Mstpyt/DPG-Examples/blob/main/drag_and_drop_project_chart.py) | [DPG GUI designer](https://github.com/shreenivasn99/dpgui-maker) | [Dear PyGui Map](https://github.com/mkouhia/dearpygui_map) | [Needle article](https://www.kcl.ac.uk/news/ultrasonic-tracking-novel-technology-identifies-tip-of-surgical-needle-during-surgeries) | [Matplotlib graph](https://github.com/RavenLabsNH/DekaDynoGUI) | [Hyperspectral Image Acquisition](https://mdpi-res.com/d_attachment/sensors/sensors-22-02159/article_deploy/sensors-22-02159-v2.pdf) | [Deka Dyno](https://github.com/RavenLabsNH/DekaDynoGUI) | [MagicaVoxel](https://github.com/DimasVoxel/MagicaVoxel-Animation-Script) | [martin_sistemi P1125](https://github.com/sistemicorp) | [Asset builder by mathgeniuszach](https://github.com/xMGZx/asset-builder) | [Crawl-Eat-Die Pygame / DPG by DeepBrown](https://github.com/OolongJunSun/Crawl-Eat-Die-Repeat) | [Quattro's Game of Life](https://github.com/QuattroMusic/DPG-Game-Of-Life) | [Image processing node editor](https://github.com/Kazuhito00/Image-Processing-Node-Editor/blob/main/README_EN.md)

# DPG FAQ
- [How to centre (center) text or align text to the right?](https://github.com/hoffstadt/DearPyGui/issues/1111)
- [Programmatically change the active tab](https://github.com/hoffstadt/DearPyGui/discussions/1582)
- [Example using threading, Asyncio, multiprocessing](https://github.com/fIux-dev/froyo/blob/f4a4a88b8f4cc910ecd9896aabacd5b71e3a76bd/source/engine.py)
- [Alternative file picker/browser dialogue | xdialog](https://github.com/xMGZx/xdialog)

# Project ideas
- Music Quiz app
- An SVG editor to create code snippets for GitHub
- A screenshot maker / editor for capturing DPG screenshots
- DPG examples
- Data analysis tool with Vaex

# Code snippets

High DPI on Windows

```Python
import ctypes
# Include the following code before showing the viewport/calling `dearpygui.dearpygui.show_viewport`.
ctypes.windll.shcore.SetProcessDpiAwareness(2)
# You will likely need to increase the font size of the font you are using if this works. Let me know if it does. 
```

Remove the maximize button on Windows

```Python

import win32api
import win32con
import win32gui
from dearpygui.dearpygui import *

def disable_cb():
    hwnd = win32gui.GetForegroundWindow()
    win32api.SetWindowLong(hwnd, win32con.GWL_STYLE,
                  win32api.GetWindowLong(hwnd, win32con.GWL_STYLE) & ~win32con.WS_MAXIMIZEBOX)

def enable_cb():
    hwnd = win32gui.GetForegroundWindow()
    win32api.SetWindowLong(hwnd, win32con.GWL_STYLE,
                  win32api.GetWindowLong(hwnd, win32con.GWL_STYLE) | win32con.WS_MAXIMIZEBOX)

create_context()
setup_registries()  # deprecated
create_viewport()
setup_dearpygui()
show_viewport()

with window():
    add_text(default_value="for hoffi")
    add_button(label="disable maximize", callback=disable_cb)
    add_button(label="enable", callback=enable_cb)
while is_dearpygui_running():
    render_dearpygui_frame()
destroy_context()
```

```Python
# Only update DPG when user changes something, on value changes and not render a frame at 60 FPS all the time
https://dearpygui.readthedocs.io/en/latest/reference/dearpygui.html#dearpygui.dearpygui.configure_app

dpg.configure_app(wait_for_input=True) to only update/render on user input!
```

```Python
# formatting text input with Python formatting
                    dpg.add_input_float(tag='tag_1',
                                        label="  ",
                                        format="%9.3f")
```

```Python
# hide values in a graph, chart, plot
# just add format="" as an argument
```
 
# GUI
- [r/learnython GUI list](https://www.reddit.com/r/learnpython/wiki/faq)
- [Overview of Python GUIs](https://wiki.python.org/moin/GuiProgramming)
- [Dear PyGui](https://github.com/hoffstadt/DearPyGui)
- [Tkinter](https://docs.python.org/3/library/tk.html)
- [PyGObject](https://pygobject.readthedocs.io/en/latest/)
- [EEL](https://github.com/ChrisKnott/Eel)
- [Gooey - based on WxPython](https://github.com/chriskiehl/Gooey)
- [WxPython Phoenix](https://github.com/wxWidgets/Phoenix)
- [Remi](https://github.com/dddomodossola/remi)
- [PySimpleGui](https://pysimplegui.readthedocs.io/en/latest/)
- [RenPy](https://www.renpy.org/)


# Web frameworks
- [FastAPI](https://fastapi.tiangolo.com/)
- [Flask](https://github.com/pallets/flask)
- [Django](https://github.com/django/django)


# Audio
- [PyMiniAudio](https://github.com/irmen/pyminiaudio) - Stable audio player, Streams audio (MP3, FLAC, WAV). API is a bit difficult, see RMP for implementation example. Simple pip install, no dependencies. Because audio is streamed and not loaded into memory, there is a slight startup delay, so not suitable for game sounds.
- [ Just_playback](https://github.com/cheofusi/just_playback) - audio player, also based on MiniAudio, with more convenient Python functions, including volume control and pause function. | [ Example implementation: Maestro CLI](https://github.com/PrajwalVandana/maestro-cli/blob/master/maestro.py)
- [PlaySound2](https://pypi.org/project/playsound2/) - Basically PlaySound, but with an important bug fix. Simple pip install.
- [AudioPlayer](https://github.com/mjbrusso/audioplayer/tree/v0.7) - Probably easiest API. Has library dependencies. Make sure to use version 0.7, not master branch.
- [Spotify Pedalboard](https://github.com/spotify/pedalboard)
- [Pygame Drum machine](https://www.youtube.com/watch?v=F3J3PZj0zi0&feature=youtu.be)
- [DawDreamer](https://github.com/DBraun/DawDreamer)
- [JUCE](https://github.com/juce-framework/JUCE)
- [Librosa](https://librosa.org/)
- [PyDub using FFMPEG](https://github.com/jiaaro/pydub/) - WAV and MP3 support built in. Other formats using FFMPEG

# Packaging Python apps
- [Nuitka](https://nuitka.net/)
- [Pyinstaller]()
- [Auto Py2Exe](https://pypi.org/project/auto-py-to-exe/)
- [Whitebox (MacOS)](http://s.sudre.free.fr/Software/Packages/about.html)
- [PyOxidizer](https://github.com/indygreg/PyOxidizer) | Rust wrapper around Python
- [Inno Setup](https://jrsoftware.org/isinfo.php) Installer for Windows


## Image editing
- Gimp
- Krita
- Inkscape
- [Online SVG optimizer](https://www.svgviewer.dev/)
- [Make badges](https://img.shields.io/badge/make-badge-blue)


##  Creating video and GIFs
- [EasyGif](https://ezgif.com/video-to-gif)
- ScreenToGif (no audio)
- ShareX
- [OBS](https://obsproject.com/)
- [VidCutter video editor](https://github.com/ozmartian/vidcutter)
- [Automatic typing for tutorials](https://github.com/mfitzp/diffcast)


# Programming tools
- PyCharm
- Sourcery
- Git


# Interesting Python projects
- [Taichi visualisation](https://github.com/taichi-dev/taichi)
- [Streamlit blog](https://blog.streamlit.io/how-to-master-streamlit-for-data-science) | [Streamlit tutorial](https://www.youtube.com/watch?v=TzF-OUA1Tlo)
- [Pretty maps](https://github.com/marceloprates/prettymaps) | [Tutorial](https://www.youtube.com/watch?v=5za5I3kUuOI) | [Colab](https://colab.research.google.com/drive/18AHHSnb0lMamHPIjMhXEezBSkP-Pn6Pq?usp=sharing)
- [CEF Python](https://github.com/cztomczak/cefpython#thanks-to-all-sponsors)
- [DaFluffyPotato Explon't Froggg game](https://dafluffypotato.itch.io/explont)


# Data management
- [Pandas](https://pandas.pydata.org/)
- [Vaex](https://vaex.io/docs/index.html/)
- [Datatable](https://datatable.readthedocs.io/en/latest/)
- [Polars](https://pola-rs.github.io/polars/py-polars/html/index.html)


# Data Exploration
- [Table Explore](https://dmnfarrell.github.io/tablexplore/)
- [Pandas GUI](https://github.com/adamerose/pandasgui)
- [MITO](https://github.com/mito-ds/monorepo)
- [Dtale](https://github.com/man-group/dtale)
- [Lux data exploration](https://github.com/lux-org/lux)
- [Autoplotter](https://www.reddit.com/r/learnmachinelearning/comments/o83zgp/autoplotter_a_gui_based_exploratory_data_analysis/) | [GitHub](https://github.com/ersaurabhverma/autoplotter)


# Data visualisation
- [Gapminder](https://www.gapminder.org/tools-offline/)
- [Datoviz](https://datoviz.org/) | [GitHub](https://github.com/datoviz/datoviz/) | [Installation](https://datoviz.org/tutorials/install/)
- [Edward Tufte](http://motioninsocial.com/tufte/#introduction)
- [Altair](https://github.com/altair-viz/altair)
- [Streamlit](https://streamlit.io/)
- [Apache Superset web](https://superset.apache.org/gallery)
- [Graph ideas, no code](https://datavizproject.com/)
- [Perspective real-time graphs web](https://perspective.finos.org/)
- [MS SandDance data exploration](https://microsoft.github.io/SandDance/)
- [Overview dataviz libraries](https://dsaber.com/2016/10/02/a-dramatic-tour-through-pythons-data-visualization-landscape-including-ggplot-and-altair/)
- [GeoPlot library](https://deepai.org/publication/geoplotlib-a-python-toolbox-for-visualizing-geographical-data)
- [PyVista](https://docs.pyvista.org/)
- [PyViz](https://pyviz.org/)
- [HoloViz](https://holoviz.org/tutorial/index.html)
- [Apache E-charts](https://echarts.apache.org/en/index.html) | [E-charts](https://github.com/apache/echarts) | [Py E-charts](https://pyecharts.org/#/en-us/charts_base)


# Network graphs
- [Cytoscape](https://cytoscape.org/what_is_cytoscape.html)
- [Gephi](https://gephi.org/)
- [Network graphs](https://schoolofdata.org/2014/08/20/4-network-visualisation-tools/)


# Fonts
- [Google fonts](https://fonts.google.com/)
- [Monospace fonts](https://ianyepan.github.io/posts/system-default-monospace-fonts-pt2/)


# Social media
- [Best time to post on Reddit](https://thebetterwebmovement.com/choosing-best-time-post-to-reddit/)
- [Top Intermediate Showcase](https://www.reddit.com/r/Python/search?q=flair_name%3A%22Intermediate%20Showcase%22&restrict_sr=1&sort=top)
- [DPG Star history graph](https://star-history.com/#hoffstadt/DearPyGui&Date)
- [GUI Star history graph](https://star-history.com/#hoffstadt/DearPyGui&pysimplegui/pysimplegui&kivy/kivy&wxWidgets/Phoenix&pygame/pygame&pythonarcade/arcade&pokepetter/ursina&panda3d/panda3d&ChrisKnott/Eel&chriskiehl/Gooey&Timeline)
- [Hacker News](https://news.ycombinator.com/news)

# Python Subreddits
- [Made in Python](https://www.reddit.com/r/madeinpython/)

- [Reddit Shadowban](https://www.reddit.com/r/ShadowBan/)

## DPG Statistics

- [PyPi download statistics](https://pypistats.org/packages/dearpygui)

[![Star History Chart](https://api.star-history.com/svg?repos=hoffstadt/DearPyGui,pysimplegui/pysimplegui,kivy/kivy,wxWidgets/Phoenix,pygame/pygame,pythonarcade/arcade,pokepetter/ursina,panda3d/panda3d,ChrisKnott/Eel,chriskiehl/Gooey&type=Timeline)](https://star-history.com/#hoffstadt/DearPyGui&pysimplegui/pysimplegui&kivy/kivy&wxWidgets/Phoenix&pygame/pygame&pythonarcade/arcade&pokepetter/ursina&panda3d/panda3d&ChrisKnott/Eel&chriskiehl/Gooey&Timeline)
