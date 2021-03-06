[![.github/workflows/main.yml](https://github.com/applibgroup/JustBar/actions/workflows/main.yml/badge.svg)](https://github.com/applibgroup/JustBar/actions/workflows/main.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=applibgroup_JustBar&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=applibgroup_JustBar)

# JustBar
A HMOS library to add a Bottom Navigation Bar.

# Source
Inspired by [Hammad Akram/JustBar](https://github.com/Hamadakram/JustBar)

## Features
1) This library provides an animation similar to Bottom navigation bar. 
2) This bar has search, chat, cart and settings icons - for demo purpose
3) Initially by default a particular icon can be highlighted.
4) The user can click on any of the icon, the icon selected will get highlighted and changes to the color specified.
5) You can configure the icons by using Red, Green and Blue colors (due to platform dependency)
6) You can configure the radius for the icons and the icons will change accordingly.

<img src="screenshots/JustBar.gif" width="500">

## Dependency
1. For using justbar module in sample app, include the source code and add the below dependencies in entry/build.gradle to generate hap/support.har.
```groovy
	dependencies {
		implementation fileTree(dir: 'libs', include: ['*.jar', '*.har'])
        	testImplementation 'junit:junit:4.13'
                ohosTestImplementation 'com.huawei.ohos.testkit:runner:1.0.0.200'
                implementation project(':justbar')
	}
```
2. For using justbar in separate application using har file, add the har file in the entry/libs folder and add the dependencies in entry/build.gradle file.
```groovy
	dependencies {
		implementation fileTree(dir: 'libs', include: ['*.har'])
		testImplementation 'junit:junit:4.13'
	}
```
3. For using justbar from a remote repository in separate application, add the below dependencies in entry/build.gradle file.
```groovy
	dependencies {
		implementation 'dev.applibgroup:justbar:1.0.0'
		testImplementation 'junit:junit:4.13'
	}
```

## Usage
#### Include following code in your layout:
```xml
    <com.irozon.justbar.JustBar
            ohos:id="$+id:bottomBar"
            ohos:width="match_parent"
            ohos:height="match_content"
            ohos:bottom_margin="16vp">
            <com.irozon.justbar.BarItem
                ohos:id="$+id:barItem"
                ohos:width="0vp"
                ohos:height="0vp"
                app:icon="$graphic:ic_search"
                app:radius="35vp" />
            .
            .
            .
    </com.irozon.justbar.JustBar>
```
Attribute | Description
--- | ---
`selectedColor` | Selected state color for the ` BarItem `
`unSelectedColor` | Unselected state color for the `BarItem`
`selectedIconColor` | Selected state color for the icon
`unSelectedIconColor` | Unselected state color for the icon
`selected` | Initial selected or unselected state for BarItem`
`icon` | Icon for `BarItem`
`radius` | Radius for the `BarItem`

Note: The user can only enter Red, Green and Blue colors for the attributes selectedColor, unSelectedColor, selectedIconColor and unSelectedIconColor because of the limitation mentioned in the FutureWork section

#### Action for `BarItem`:
```java
    justBar.setOnBarItemClickListener(new OnBarItemClickListener() {
               @Override
               public void onBarItemClick(BarItem barItem, int position) {
                    // Your code here
               }
           });
```

## Future Work
Since there is no alternate api for setColorFilter in HMOS platform, custom attributes - app:selectedColor, 
app:unSelectedColor, app:selectedIconColor, app:unSelectedIconColor are supported for limited colors because of platform dependency (not all the colors like in android). 
As a result, user needs to call the createColorMatrix function and pass a colorCode as an argument which will internally call setColorMatrix(createColorMatrix(selectedColor)) to change the color of the drawable. Once HMOS platform supports setColorFilter, then this custom attribute can be included.
Due to unavailability of similar api as applyTransformation() in HarmonyOS platform, the animation behaviour is not exactly the same as android base library but it is similar.
                                                                                                   
## Licence
```
Copyright 2018 Irozon, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```                                                                                   

