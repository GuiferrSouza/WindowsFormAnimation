# WindowsFormAnimation

`WindowsFormAnimation` is a .NET library designed to facilitate animations within Windows Forms applications. It provides a simple interface to animate windows using various effects such as sliding, fading, and more.

## Features

- **Animate Windows**: Easily apply animations to any window handle.
- **Customizable Animations**: Set the duration and type of animation.
- **Event Handling**: Hook into animation start and end events.

## Installation

To use `WindowsFormAnimation`, simply include the library in your project.

## Usage

### Animation Class

The `Animation` class represents an animation with customizable properties.

#### Properties

- `int Duration`: The duration of the animation in milliseconds.
- `AnimationFlags Flags`: The type of animation to apply.
- `string Name`: The name of the animation.

#### Events

- `event Action<Animation> AnimationStarted`: Triggered when the animation starts.
- `event Action<Animation> AnimationEnded`: Triggered when the animation ends.

#### Methods

- `void OnStarted()`: Triggers the `AnimationStarted` event.
- `void OnEnded()`: Triggers the `AnimationEnded` event.

#### AnimationFlags Enum

Defines the types of animations available:

- `Show`
- `Hide`
- `Slide`
- `Fade`
- `Center`
- `RightToLeft`
- `LeftToRight`
- `TopToBottom`
- `BottomToTop`

### Animator Class

The `Animator` class is responsible for playing animations on window handles.

#### Methods

- `void Play(IntPtr hwnd, Animation animation)`: Plays the specified animation on the given window handle.

#### Events

- `event Action<Animation> AnimationStarted`: Triggered when an animation starts.
- `event Action<Animation> AnimationEnded`: Triggered when an animation ends.

## Example

```csharp
using System;
using WindowsFormAnimation;

class Program
{
    static void Main()
    {
        IntPtr hwnd = // Obtain window handle
        var animation = new Animation
        {
            Duration = 1000,
            Flags = Animation.AnimationFlags.Fade | Animation.AnimationFlags.Center,
            Name = "FadeInCenter"
        };

        var animator = new Animator();
        animator.AnimationStarted += (anim) => Console.WriteLine($"{anim.Name} started.");
        animator.AnimationEnded += (anim) => Console.WriteLine($"{anim.Name} ended.");

        animator.Play(hwnd, animation);
    }
}
```

## Liscence

This project is licensed under the MIT License. See the LICENSE file for details.