# Android

The first software stack we started with is Android. It's been a long journey since the days of Android Eclair. We've seen how the ecosystem has grown from an operating system designed to only work on phones to tablets and other form factors.

Over the years there have been a number of guidelines published. Some suggested prefixing every private variable with an `m` \(never understood how this improves readability\).

Here are a few guidelines and practices we follow:

* [Project Structure](android.md#project-structure)
  * [Class files](android.md#class-files)
  * [Resource files](android.md#resource-files)
  * [XML style guidelines](android.md#xml-style-guidelines)
* [Nomenclature \(Java\)](android.md#nomenclature-java)
* [Nomenclature \(Kotlin\)](android.md#nomenclature-kotlin)
* [Best Practices](android.md#best-practices)

## Project Structure

All new projects should start with the gradle build system. Please use the latest Android studio to create a new project.

### Class files

All class files should be written in `UpperCamelCase`. Class files that extend system classes should have use the system class name as a suffix.

**Preferred**

```text
public class WednesdayActivity extends Activity {}
```

**Not Preferred**

```text
public class Wednesday extends Activity {}
```

### Resource Files

All resources files are written in `snake_case`

* **Drawable**

Please follow these naming conventions for drawables:

| Asset Type | Prefix | Example |
| :--- | :--- | :--- |
| Icon | ic\_ | ic\_wednesday.png |
| Button | btn\_ | btn\_wednesday.png |
| Dialog | dialog\_ | dialog\_wednesday.png |
| Menu | menu\_ | menu\_wednesday.png |
| Notification | notification\_ | notification\_wednesday.png |
| Tabs | tab\_ | tab\_wednesday.png |

* **Layout**

Please follow these naming convention for layout files:

| System Class | Class Name | Example |
| :--- | :--- | :--- |
| Activity | WednesdayActivity | activity\_wednesday.xml |
| Fragment | WednesdayFragment | fragment\_wednesday.xml |
| Dialog | WednesdayDialog | diaglog\_wednesday.xml |
| Adapter Item | -NA- | item\_wednesday.xml |
| Partial | -NA- | partial\_wednesday.xml |

For the last two the suffix `wednesday` would be replaced by a name that is more apt to your use case.

* **Selector States**

| State  | Suffix | Example |
| :--- | :--- | :--- |
| Pressed | \_pressed | btn\_wednesday\_pressed.png |
| Focussed | \_focussed | btn\_wednesday\_focussed.png |
| Selected | \_selected | btn\_wednesday\_selected.png |
| Checked | \_checked | btn\_wednesday\_checked.png |
| Disabled | \_disabled | btn\_wednesday\_disabled.png |

* **Menu**

Considering all menu resources are in the `menu` folder. Don't suffix these with the `_menu` string.

For example the menu for the `WednesdayActivity` should be named `activity_wednesday.xml`

* **Values**

We prefer to follow the default android naming convention. Resource files like strings, values are always named in plural.

### XML Style Guidelines

* While defining parameters of a view please follow this order:
  * `id` 
  * Style
  * All other parameters

**Preferred**

```text
<TextView
  android:id:"@+id/text_view_wednesday"
  android:style="@+style/StyleTextView"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content" />
```

**Not Preferred**

```text
<TextView
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:id:"@+id/text_view_wednesday"
  android:style="@+style/StyleTextView" />
```

* Prefix all `id` 's with a string that declares the name of the `View`.

**Preferred**

```text
android:id="@+id/text_view_wednesday"
```

**Not Preferred**

```text
android:id="@+id/wednesday_text"
```

* Please define all styles using upper camel case syntax.

**Preferred**

```text
android:style="@+style/WednesdayText"
```

**Not Preferred**

```text
android:style="@+style/wednesday_text"
```

## Nomenclature \(Java\)

We follow the same Java Style Guide that google prescribes. You can find it here: [https://google.github.io/styleguide/javaguide.html](https://google.github.io/styleguide/javaguide.html)

## Nomenclature \(Kotlin\)

We follow the Kotlin Style guide that is endorsed by google. You can find it here: [https://developer.android.com/kotlin/style-guide](https://developer.android.com/kotlin/style-guide)

## Best Practices

We like to follow the reactive principle where our application logic reacts to change either from a user generated event or a change in the underlying data.

Google has done an amazing job of describing the best practices to ensure your app is testable, reusable and robust. Please head here to know more: [https://developer.android.com/jetpack/docs/guide](https://developer.android.com/jetpack/docs/guide)

We use the following libraries in our applications:

* [Retrofit](https://square.github.io/retrofit/)
* [Glide](https://github.com/bumptech/glide)
* [Android Architecture components](https://developer.android.com/topic/libraries/architecture)
* [Dagger](https://github.com/google/dagger)
* [Kodein](https://github.com/Kodein-Framework/Kodein-DI)

Please ensure you write espresso and unit tests for the features you build.

