# Xablu.Walkthrough
The Xablu WebApiClient is a C# HTTP library which aims to simplify consuming of Web API services in .NET projects.

### Setup & Usage
* Available on NuGet: https://www.nuget.org/packages/Xablu.Walkthrough/
* Install into each project that utilizes the WebApiClient

### Build Status: 
[![Build status](https://ci.appveyor.com/api/projects/status/5ey0sq4fn01t9o56?svg=true
)](https://ci.appveyor.com/project/Xablu/xablu-webapiclient)
![GitHub tag](https://img.shields.io/github/tag/Xablu/Xablu.WebApiClient.svg)
[![NuGet](https://img.shields.io/nuget/v/Xablu.WebApiClient.svg?label=NuGet)](https://www.nuget.org/packages/Xablu.WebApiClient/)
[![MyGet](https://img.shields.io/myget/xabluhq/v/Xablu.WebApiClient.svg)](https://www.myget.org/F/Xablu.WebApiClient/api/v2)

# Containers & Pages

The plugin works with themes. Every theme must consist of a Container and a Page. Containers and Pages can be mixed and matched. The current available containers and pages are:

| ForestPrimes container and page| Pantheon container and ForestPage | Vesta container and page  |
| ------------------------------ |-----------------------------------| ------------------------- |
| ![ForestPrimes](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/fullforest.png) | ![Pantheon](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/pantheonforest.png) |![Vesta](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/fullvesta.png) |
| ![ForestPrimes](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/fullforest-android.png) | ![Pantheon](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/pantheonforest-android.png) | ![Vesta](https://github.com/Xablu/Xablu.Walkthrough/raw/master/resources/vesta-android.png) |

# Usage

After you have installed the nuget into every project simple create a new theme in your PCL library like so:

```c#
var theme = new Theme<ForestPrimesPage, ForestPrimesContainer>();
```

Now style your container the way you like, for example:

```c#
 theme.Container = new ForestPrimesContainer()
            {
                StartButtonControl = new ButtonControl()
                {
                    Text = "START",
                    BackgroundColor = Color.FromArgb(0, 237, 26, 59)
                },
                NextButtonControl = new ImageButtonControl()
                {
                    Image = "ArrowRight",
                    ClickAction = () => CrossWalkthrough.Current.Next()
                }
            };
```
Add as much pages to the theme as you like:
```c#
            theme.Pages.Add
                 (
                      new ForestPrimesPage()
                      {
                          BackgroundColor = Color.FromArgb(239, 239, 239),
                          TitleControl = new TextControl()
                          {
                              Text = "Take advantage now!",
                              TextSize = 24
                          },
                          ImageControl = new ImageControl()
                          {
                              Image = "xablu"
                          },
                          DescriptionControl = new TextControl()
                          {
                              Text = "Don't build it yourself, use the XABLU plugin! It's easy to extend and implement!",
                              TextSize = 16
                          }
                      }
                    );
```

Next call the setup method and show it:

```c#
CrossWalkthrough.Current.Setup(theme);
CrossWalkthrough.Current.Show();
```

