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

# DPG apps

- [Game of life - High DPI](https://github.com/DataExplorerUser/game_of_life_high_DPI)
- [Midi Explorer](https://github.com/EMATech/midiexplorer/)
- [turnroot tactical RPGs](https://github.com/josephclaytonhansen/turnroot/tree/main/dpg)
- [Athena Game Library](https://github.com/DirectiveAthena/AthenaDPGLib)
- [martin_sistemi P1125](https://github.com/sistemicorp)
- [Trading bot](https://github.com/Gus-The-Forklift-Driver/TradingBotV2)
- [3D Stable Dreamfusion](https://github.com/ashawkey/stable-dreamfusion#stable-dreamfusion)
- [Dreamfields torch](https://github.com/ashawkey/dreamfields-torch)


# Small DPG apps
- [DekaGUI](https://github.com/RavenLabsNH/DekaDynoGUI/issues/3#issuecomment-1225876065) | Demo with data stream with multiprocessing + Matplotib
- [Calculator](https://github.com/Fus3n/dpg-calc)
- [Image to PDF converter](https://gitlab.com/mr-fox-h/FDF)
- [Lens simulation](https://github.com/yslib/Cameray)
- [Algorithm visualiser](https://github.com/Anurag-gg/Algorithm-visualizer)
- [Registration system](https://github.com/carlobeni/Registration-System-with-DearPyGui-in-python)
- [Sorting visualizer](https://github.com/YunusMaranki/SortingVisualizer)
- [Video format converter](https://github.com/philliphqs/allconv)
- [ez Notes](https://github.com/Brandon82/DPG-ezNotes)
- [cForm](https://github.com/ReaseRZ/CForm)

# DPG FAQ
- [How to centre (center) text or align text to the right?](https://github.com/hoffstadt/DearPyGui/issues/1111)
- [Programmatically change the active tab](https://github.com/hoffstadt/DearPyGui/discussions/1582)
- [Example using threading, Asyncio, multiprocessing](https://github.com/fIux-dev/froyo/blob/f4a4a88b8f4cc910ecd9896aabacd5b71e3a76bd/source/engine.py)
- [Alternative file picker/browser dialogue | xdialog](https://github.com/xMGZx/xdialog)
- [Coloured words in one sentence example](https://github.com/DataExplorerUser/coloured_words)
- [Sistemi DPG code patterms](https://github.com/sistemicorp/b13-DPG_Code_patterns)
- [Drag and drop Project mgt](https://github.com/Mstpyt/DPG-Examples/blob/main/drag_and_drop_project_chart.py)
- [Searchable tag record](https://github.com/sharkbound/pythontools/tree/master/examples/dearpyguiapps/index_ui)


# Project ideas
- Music Quiz app
- An SVG editor to create code snippets for GitHub
- A screenshot maker / editor for capturing DPG screenshots
- DPG examples
- Data analysis tool with Vaex
- OpenCV image editor (various blurs and options using sliders, before & after image)

# Code snippets

- [Personal classes Marcus Castelo](https://github.com/marcuscastelo/dpgext)

Theme padding in x and y direction
```Python
# When applying theme settings, e.g. padding, by default it affects the horizontal direction. For example, when using:

    dpg.add_theme_style(dpg.mvStyleVar_FramePadding, 5, category=dpg.mvThemeCat_Core)

# How do you apply the padding in the vertical direction?
# Theme style elements have x and y arguments. Here, 5 is filling x.

    dpg.add_theme_style(dpg.mvStyleVar_FramePadding, x=5, category=dpg.mvThemeCat_Core)
    dpg.add_theme_style(dpg.mvStyleVar_FramePadding, y=10, category=dpg.mvThemeCat_Core)
    dpg.add_theme_style(dpg.mvStyleVar_FramePadding, x=5, y=10, category=dpg.mvThemeCat_Core) # does that work?
    
```

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

```python
# Select table cell and get data
import dearpygui.dearpygui as dpg

dpg.create_context()
dpg.create_viewport(width=800, height=450)
dpg.setup_dearpygui()

with dpg.theme() as global_theme:
    with dpg.theme_component(dpg.mvTable):
        dpg.add_theme_color(dpg.mvThemeCol_HeaderHovered, (255, 0, 0, 100), category=dpg.mvThemeCat_Core)
        dpg.add_theme_color(dpg.mvThemeCol_HeaderActive, (0, 0, 0, 0), category=dpg.mvThemeCat_Core)
        dpg.add_theme_color(dpg.mvThemeCol_Header, (0, 0, 0, 0), category=dpg.mvThemeCat_Core)

dpg.bind_theme(global_theme)


def clb_selectable(sender, app_data, user_data):
    print(f"Row {user_data}")


with dpg.window(tag="Table"):
    with dpg.table(header_row=True, callback=lambda: print("callback!!!")):
        dpg.add_table_column(label="First")
        dpg.add_table_column(label="Second")
        dpg.add_table_column(label="Third")

        for i in range(20):
            with dpg.table_row():
                for j in range(3):
                    dpg.add_selectable(label=f"Row{i} Column{j}", span_columns=True, callback=clb_selectable, user_data=i)

dpg.show_viewport()
dpg.set_primary_window("Table", True)
dpg.start_dearpygui()
dpg.destroy_context()
```

```python
# Select table row callback
import dearpygui.dearpygui as dpg

dpg.create_context()
dpg.create_viewport(width=800, height=450)
dpg.setup_dearpygui()

with dpg.theme() as global_theme:
    with dpg.theme_component(dpg.mvTable):
        dpg.add_theme_color(dpg.mvThemeCol_HeaderHovered, (255, 0, 0, 100), category=dpg.mvThemeCat_Core)
        dpg.add_theme_color(dpg.mvThemeCol_HeaderActive, (0, 0, 0, 0), category=dpg.mvThemeCat_Core)
        dpg.add_theme_color(dpg.mvThemeCol_Header, (0, 0, 0, 0), category=dpg.mvThemeCat_Core)

dpg.bind_theme(global_theme)


def clb_selectable(sender, app_data, user_data):
    print(f"Content:{dpg.get_item_label(sender)}, Row and column: {user_data}")


with dpg.window(tag="Table"):
    with dpg.table(header_row=True, callback=lambda: print("callback!!!")):
        dpg.add_table_column(label="First")
        dpg.add_table_column(label="Second")
        dpg.add_table_column(label="Third")

        for i in range(20):
            with dpg.table_row():
                for j in range(3):
                    dpg.add_selectable(label=f"Row{i} Column{j}", callback=clb_selectable, user_data=(i,j))

dpg.show_viewport()
dpg.set_primary_window("Table", True)
dpg.start_dearpygui()
dpg.destroy_context()
```

```python
# Updating listbox after creation DPG
import dearpygui.dearpygui as dpg

def new_list_box_item():
    listbox = dpg.get_item_configuration("lbox")['items']
    listbox.append(str(len(listbox)+1))
    dpg.configure_item("lbox", items=listbox)

dpg.create_context()
dpg.create_viewport(title='Custom Title', width=600, height=300)
with dpg.window(label="Example Window"):
    dpg.add_listbox(items=['1', '2'], tag="lbox")
    dpg.add_button(label="New listbox_item", callback=new_list_box_item)

dpg.show_metrics()
dpg.setup_dearpygui()
dpg.show_viewport()
dpg.start_dearpygui()
dpg.destroy_context()
```

```Python
# center / centre a window in DPG
def render_window_center(sender, app_data, user_data):
    if dpg.does_item_exist(user_data):
        main_width = dpg.get_viewport_width()
        main_height = dpg.get_viewport_height()
        login_width = dpg.get_item_width(user_data)
        login_height = dpg.get_item_height(user_data)
        dpg.set_item_pos(user_data, [int((main_width // 2 - login_width // 2)),
                                     int((main_height / 2 - login_height / 2))])

with window() as window_auth:
    with dpg.group(horizontal=True):
        dpg.add_text()
        dpg.add_input_text()
    with dpg.item_handler_registry(tag=dpg.generate_uuid()) as handler:
        dpg.add_item_visible_handler(callback=render_window_center, parent=handler, user_data=window_auth)
    dpg.bind_item_handler_registry(item=window_auth, handler_registry=handler)
```

```Python
# I have problem with letters "ёЁ". When I try to write "ё", I get "¸". How can i fix this?
# support for Ukrainian (cyrillic) characters (to console)

# chars_remap = {OLD: NEW}
chars_remap = {0x00A8: 0x0401,  # Ё
               0x00B8: 0x0451,  # ё
               0x00AF: 0x0407,  # Ї
               0x00BF: 0x0457,  # ї
               0x00B2: 0x0406,  # І
               0x00B3: 0x0456,  # і
               0x00AA: 0x0404,  # Є
               0x00BA: 0x0454}  # є
with dpg.font_registry():
    with dpg.font("{FONT}", 20) as default_font:
        dpg.add_font_range_hint(dpg.mvFontRangeHint_Default)
        dpg.add_font_range_hint(dpg.mvFontRangeHint_Cyrillic)
        biglet = remap_big_let  # Starting number for remapped cyrillic alphabet
        for i1 in range(big_let_start, big_let_end + 1):  # Cycle through big letters in cyrillic alphabet
            dpg.add_char_remap(i1, biglet)  # Remap the big cyrillic letter
            dpg.add_char_remap(i1 + alph_len, biglet + alph_len)  # Remap the small cyrillic letter
            biglet += 1  # choose next letter
        for char in chars_remap.keys():
            dpg.add_char_remap(char, chars_remap[char])

with dpg.window(label="Тест", height=200, width=200):
    def to_cyr(instr):  # conversion function
        out = []  # start with empty output
        for i in range(0, len(instr)):  # cycle through letters in input string
            if ord(instr[i]) in chars_remap:
                out.append(chr(chars_remap[ord(instr[i])]))
            elif ord(instr[i]) in range(big_let_start, small_let_end + 1):  # check if the letter is cyrillic
                out.append(chr(ord(instr[i]) + alph_shift))  # if it is change it and add to output list
            else:
                out.append(instr[i])
        return ''.join(out)
```

```Python
# Currency graphs

import dearpygui.dearpygui as dpg
from Giang_Project.forex_workspace.forex_lib.lib import *
from dpg_theme_config import style
dpg.create_context(); style()

# ----------------------------------------------------------------------------------------------------------------------
ccy_ = ["AUD", "CAD", "CHF", "EUR", "GBP", "JPY", "NZD", "USD"]
ccy_7 = ["AUD", "CAD", "CHF", "EUR", "GBP", "JPY", "NZD"]
plot_, x_axis_, y_axis_, bar_, bar_theme_ = [], [], [], ["bar_series" + str(i) for i in range(0, 7)], []
color = [[0, 128, 000, 255], [139, 69, 19, 255], [255, 255, 000, 255], [255, 105, 150, 255],
         [220, 20, 60, 255], [153, 50, 204, 255], [100, 149, 237, 255], [255, 255, 255, 255]]

with dpg.theme() as ema_theme_:
    with dpg.theme_component():
        dpg.add_theme_color(dpg.mvPlotCol_Line, [255, 150, 50, 255], category=dpg.mvThemeCat_Plots)
for i in color:
    with dpg.theme() as theme:
        with dpg.theme_component():
            dpg.add_theme_color(dpg.mvPlotCol_Line, i, category=dpg.mvThemeCat_Plots)
            dpg.add_theme_color(dpg.mvPlotCol_Fill, i, category=dpg.mvThemeCat_Plots)
            dpg.add_theme_color(dpg.mvThemeCol_FrameBg, i, category=0)
    bar_theme_.append(theme)
# bar_theme_.pop() after bind checkbox

with dpg.window(label="EMA 200 DashBoard", tag="primary_window", width=800, height=600,
                no_close=True, no_resize=True, no_move=True):
    with dpg.group(horizontal=True):  # select base currency
        for i in range(0, 8):
            dpg.add_checkbox(label=ccy_[i], tag=ccy_[i]+"_checkbox_", default_value=False)
            print(ccy_[i])
            dpg.bind_item_theme(ccy_[i]+"_checkbox_", bar_theme_[i])
            dpg.add_spacer(width=30)
        dpg.configure_item("USD_checkbox_", default_value=True)
        bar_theme_.pop()
    with dpg.group(horizontal=True):
        dpg.add_text("bars")
        dpg.add_input_text(width=50, default_value="1000", on_enter=True, tag="bars_input_")
        dpg.add_input_text(width=50, default_value="H1", on_enter=True, tag="timeframe_input_")
        dpg.add_spacer(width=30)
        dpg.add_text("EMA period: ")
        dpg.add_input_text(width=50, default_value="50", on_enter=True, tag="ema_period_input")

    # with dpg.child_window(width=1000, height=1400):
    def drag_point_callback(sender, app_data, user_data):
        for i in range(0, 7):
            if dpg.get_item_alias(sender)[-1] == i:
                pass

            close_ = rate_close(symbol=dpg.get_value("symbol_input"), tf=dpg.get_value("timeframe_input_"),
                                bars=int(dpg.get_value("bars_input_")), source="close")
            if dpg.get_item_alias(sender)[20:24] == "main":
                dpg.configure_item("vertical_drag_point_main" + str(i), default_value=dpg.get_value(sender))
                dpg.configure_item("horizontal_drag_point_chart", default_value=close_[round(dpg.get_value(sender))])
            if dpg.get_item_alias(sender)[20:25] == "begin":
                dpg.configure_item("vertical_drag_point_begin" + str(i), default_value=dpg.get_value(sender))
            if dpg.get_item_alias(sender)[20:23] == "end":
                dpg.configure_item("vertical_drag_point_end" + str(i), default_value=dpg.get_value(sender))
    for i in range(0, 7):
        with dpg.child_window(tag="EMA_" + str(i), width=1000, height=180, no_scrollbar=True, border=False):
            with dpg.plot(label="", tag="plot_" + str(i),
                          width=-1, height=-1,
                          no_title=True, no_menus=True, no_box_select=True, no_mouse_pos=False,
                          no_highlight=False, no_child=False, query=False, crosshairs=False,
                          anti_aliased=True, equal_aspects=False):
                dpg.add_drag_line(label="", default_value=0, vertical=False, thickness=4, color=[255, 0, 0, 255])

                dpg.add_drag_line(label="", tag="vertical_drag_point_main" + str(i),
                                  default_value=0, vertical=True, thickness=2, color=[255, 255, 255, 255])

                dpg.add_drag_line(label="", tag="vertical_drag_point_begin" + str(i),
                                  default_value=0, vertical=True, thickness=2, color=[0, 0, 255, 255])
                dpg.add_drag_line(label="", tag="vertical_drag_point_end" + str(i),
                                  default_value=0, vertical=True, thickness=2, color=[0, 0, 255, 255])

                dpg.set_item_callback("vertical_drag_point_main" + str(i), callback=lambda s, a, u: [
                    drag_point_callback(s, a, u), dpg.configure_item(
                        "vertical_drag_point_chart", default_value=dpg.get_value(s))])
                dpg.set_item_callback("vertical_drag_point_begin" + str(i), drag_point_callback)
                dpg.set_item_callback("vertical_drag_point_end" + str(i), drag_point_callback)

                with dpg.plot_axis(dpg.mvXAxis, label="", tag="X_" + str(i),
                                   no_tick_labels=True, no_gridlines=True, no_tick_marks=True): pass
                with dpg.plot_axis(dpg.mvYAxis, label="", tag="Y_" + str(i),
                                   no_tick_labels=True, no_gridlines=True, no_tick_marks=True):
                    dpg.add_bar_series(x=[0, 1, 2], y=[0, 1, 2], tag="bar_series" + str(i))

        plot_.append("EMA_" + str(i))
        x_axis_.append("X_" + str(i))
        y_axis_.append("Y_" + str(i))
        bar_.append("bar_series" + str(i))


    def update_chart():  # no s, a, u
        high_ = rate_close(symbol=dpg.get_value("symbol_input"), tf=dpg.get_value("timeframe_input_"),
                           bars=int(dpg.get_value("bars_input_")), source="high")
        low_ = rate_close(symbol=dpg.get_value("symbol_input"), tf=dpg.get_value("timeframe_input_"),
                          bars=int(dpg.get_value("bars_input_")), source="low")
        # close_ = rate_close(symbol=dpg.get_value("symbol_input"), tf=dpg.get_value("timeframe_input_"),
        #                     bars=int(dpg.get_value("bars_input_")), source="close")
        # ema_ = ta.EMA(np.array(close_), int(dpg.get_value("ema_period_input")))
        dpg.configure_item("high_line", x=[x for x in range(len(high_))], y=high_)
        dpg.configure_item("low_line", x=[x for x in range(len(low_))], y=low_)
        dpg.configure_item("ema_high_line", x=[x for x in range(len(low_))],
                           y=ta.EMA(np.array(high_), int(dpg.get_value("ema_period_input"))))
        dpg.configure_item("ema_low_line", x=[x for x in range(len(low_))],
                           y=ta.EMA(np.array(low_), int(dpg.get_value("ema_period_input"))))
        dpg.fit_axis_data("X_main")
        dpg.fit_axis_data("Y_main")
    def refresh_ema(sender=None, app_data=None, user_data=None):
        bars = int(dpg.get_value("bars_input_"))
        time_frame = dpg.get_value("timeframe_input_")
        ema_period = int(dpg.get_value("ema_period_input"))
        print(bars, time_frame)
        for a, b, c, d, e, f, g in zip(plot_, x_axis_, y_axis_, bar_, ccy_7, [str(_) for _ in range(0, 7)], bar_theme_):
            if not mt5.initialize(r"C:\Program Files\FBS MetaTrader 5\terminal64.exe"):
                _ = [print("initialize() failed, error code =", mt5.last_error()), mt5.shutdown()]
            if e == "CHF" or e == "JPY" or e == "CAD":
                data_high = rate_close("USD" + e, bars=bars, tf=time_frame, source="high")
                data_high = [1 / x for x in data_high]
                data_low = rate_close("USD" + e, bars=bars, tf=time_frame, source="high")
                data_low = [1 / x for x in data_low]
                data_close = rate_close("USD" + e, bars=bars, tf=time_frame, source="close")
                data_close = [1 / x for x in data_close]
            else:
                data_high = rate_close(e + "USD", bars=bars, tf=time_frame, source="high")
                data_low = rate_close(e + "USD", bars=bars, tf=time_frame, source="low")
                data_close = rate_close(e + "USD", bars=bars, tf=time_frame, source="close")

            ema_200 = ta.EMA(np.array(data_close), ema_period)
            # final_ = [x - y for x, y in zip(data_close, ema_200)]
            final_ = [h_ - e_ if c_ > e_ else l_ - e_ for h_, l_, c_, e_ in zip(data_high, data_low, data_close, ema_200)]

            if dpg.does_item_exist(d):
                dpg.delete_item(d)
                print("ok")
            dpg.add_bar_series(x=[z for z in range(0, bars)], y=final_, tag="bar_series" + str(f), parent=c)
            dpg.bind_item_theme("bar_series" + str(f), g)
            dpg.fit_axis_data(b)
            dpg.fit_axis_data(c)
            update_chart()

    def update_drag_point():
        for i in range(0, 7):
            dpg.configure_item("vertical_drag_point_main" + str(i), default_value=int(dpg.get_value("bars_input_")) / 2)
            dpg.configure_item("vertical_drag_point_begin" + str(i), default_value=int(dpg.get_value("ema_period_input")))
            dpg.configure_item("vertical_drag_point_end" + str(i), default_value=int(dpg.get_value("bars_input_")) -
                               int(dpg.get_value("bars_input_")))

    dpg.set_item_callback("bars_input_", callback=lambda s, a, u: [update_drag_point(), refresh_ema(s, a, u)])
    dpg.set_item_callback("timeframe_input_", callback=lambda s, a, u: [update_drag_point(), refresh_ema(s, a, u)])
    dpg.set_item_callback("ema_period_input", callback=lambda s, a, u: [update_drag_point(), refresh_ema(s, a, u)])

with dpg.window(label="Chart", tag="main_chart", width=3000, height=650, pos=[0, 1350],
                no_resize=True, no_close=True, no_move=True, collapsed=False):
    with dpg.group(horizontal=True):
        dpg.add_text("Symbol: ")
        dpg.add_input_text(tag="symbol_input", width=50, default_value="EURUSD")
        dpg.add_spacer(width=50)
        dpg.add_text("DashBoard Base currency: --> ")
        dpg.add_input_text(width=50, label="", default_value="USD")
    with dpg.child_window(width=1000, height=600, border=False):
        with dpg.plot(label="", width=-1, height=-1,
                      no_title=True, no_menus=True, no_box_select=True, no_mouse_pos=False,
                      no_highlight=False, no_child=False, query=False, crosshairs=False,
                      anti_aliased=True, equal_aspects=False):
            dpg.add_drag_line(label="", tag="vertical_drag_point_chart",
                              default_value=0, vertical=True, thickness=2, color=[255, 255, 255, 255])
            dpg.add_drag_line(label="", tag="horizontal_drag_point_chart",
                              default_value=0, vertical=False, thickness=2, color=[255, 255, 255, 255])

            with dpg.plot_axis(dpg.mvXAxis, label="", tag="X_main",
                               no_tick_labels=True, no_gridlines=True, no_tick_marks=True): pass
            with dpg.plot_axis(dpg.mvYAxis, label="", tag="Y_main",
                               no_tick_labels=True, no_gridlines=True, no_tick_marks=True):
                dpg.add_line_series(x=[0, 1, 2, 3, 4], y=[0, 1, 2, 3, 4], tag="high_line", parent="Y_main")
                dpg.add_line_series(x=[0, 1, 2, 3, 4], y=[0, 1, 2, 3, 4], tag="low_line", parent="Y_main")
                dpg.add_line_series(x=[0, 1, 2, 3, 4], y=[0, 1, 2, 3, 4], tag="ema_high_line", parent="Y_main")
                dpg.add_line_series(x=[0, 1, 2, 3, 4], y=[0, 1, 2, 3, 4], tag="ema_low_line", parent="Y_main")
                dpg.bind_item_theme("high_line", bar_theme_[0])
                dpg.bind_item_theme("low_line", bar_theme_[4])
                dpg.bind_item_theme("ema_high_line", ema_theme_)
                dpg.bind_item_theme("ema_low_line", ema_theme_)

# ----------------------------------------------------------------------------------------------------------------------
dpg.create_viewport(title="EMA 200 DashBoard", width=1064, height=2107, x_pos=0, y_pos=12)
dpg.set_primary_window("primary_window", True)
with dpg.theme() as primary_window_theme:
    with dpg.theme_component(dpg.mvThemeCat_Core):
        dpg.add_theme_style(dpg.mvStyleVar_WindowBorderSize, 0, category=dpg.mvThemeCat_Core)
        dpg.bind_item_theme("primary_window", primary_window_theme)
dpg.setup_dearpygui()
dpg.show_viewport()
while dpg.is_dearpygui_running():
    dpg.render_dearpygui_frame()

# ----------------------------------------------------------------------------------------------------------------------
dpg.destroy_context()
```

```Python
# add function or other callable to list of events
# execute events based on a list
# useful for maintaining a list of events
# that should run as part of the event loop
# events can be added to or removed from
# the list at runtime

def function_1():
  print("""Let's go!""")

def function_2():
  print("""Bye!""")

events = [function_1, function_2]

for event in events:
        event()
```

```Python
# You can do so manually events = [event1, event2, ] or through other DPG callbacks.
# Instead of changing the state of a global variable and having a conditional check 
# in the main loop, you append the event to the list instead. The "state" in this 
# case is simply the callback existing in the container. 

# Clicking the button will either add  render_callback to events 
# (scheduling it to run) or will remove it.

events = [] 

def render_event():
   ... 

def button_callback():
    if render_event not in events:
        events.append(render_event)
    else:
        events.remove(render_event)

with dpg.window():
    button1 = dpg.add_button(callback=button_callback)
```

- [Play video with DPG article](https://diogoaos.medium.com/display-video-in-a-python-gui-with-dear-pygui-6649edb9fafd)
 
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
- Wasabi2D
- [p3ui](https://github.com/0lru/p3ui) | Python binding to IMGUI focused on reducing frame rates


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
- [PyAudio](https://people.csail.mit.edu/hubert/pyaudio/) - Python bindings for PortAudio v19, the cross-platform audio I/O library.
- [Muzik - music generation](https://github.com/microsoft/muzic)

# Packaging Python apps
- [Nuitka](https://nuitka.net/)
- [Pyinstaller]()
- [Auto Py2Exe](https://pypi.org/project/auto-py-to-exe/)
- [Whitebox (MacOS)](http://s.sudre.free.fr/Software/Packages/about.html)
- [PyOxidizer](https://github.com/indygreg/PyOxidizer) | Rust wrapper around Python
- [Inno Setup](https://jrsoftware.org/isinfo.php) Installer for Windows


## Image editing
- [Online UI colour picker - Coolers](https://coolors.co/)
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
- [Graphical data graph story telling](https://github.com/vizzuhq/ipyvizzu-story)


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
