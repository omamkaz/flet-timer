# Flet Timer
 
The `Timer` is a timer class
It demonstrates how to create a countdown timer using threading for real-time display updates.

## Usage

Here's an example that demonstrates how to use the `Timer`.

First, let's define a callback function that will execute at a specified interval:

```python
def update_time():
    timer_txt.value = datetime.now().strftime("%H:%M:%S")
    page.update()
```

Next, create the `Timer` object with the desired interval in seconds, a name, and the callback:

```python
timer = Timer()
```

The complete example code would look like this:

```python
import flet as ft
from flet_timer import Timer
from datetime import datetime


def main(page: ft.Page):
    page.title = "Timer Example 1"
    page.vertical_alignment = ft.MainAxisAlignment.CENTER
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER

    page.window.width = 360
    page.window.height = 600


    def update_time():
        timer_txt.value = datetime.now().strftime("%H:%M:%S")
        page.update()


    timer = Timer(callback=update_time)

    timer_txt = ft.Text(
        value=datetime.now().strftime("%H:%M:%S"), 
        text_align="center",
        size=24
    )

    page.add(
        timer_txt,
        ft.Button(
            text = "Start",
            on_click=lambda e: timer.start()
        ),
        ft.Button(
            text = "Stop",
            on_click=lambda e: timer.stop()
        ),
        ft.Button(
            text = "Pause",
            on_click=lambda e: timer.pause()
        ),
        ft.Button(
            text = "Resume",
            on_click=lambda e: timer.resume()
        )
    )

ft.app(target=main)
```

## Output of above code

![Example 1](media/example_1.png)