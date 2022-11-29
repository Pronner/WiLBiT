# ![W](https://cdn.discordapp.com/icons/873990858507186307/069985c1b4a16351efeb250bc22265be.webp?size=40)iLBiT
WiLBiT is a front-end framework used for C#.NET, VB.NET, (and maybe) C++.NET. Back-end code may apply. It is currently in **early development**, meaning features will be very few. It's only the beginning, however updates will be added frequently to this framework.

Currently, it supports **multiple controls**, with all of them having automatic **real transparency**, meaning it won't just have the Transparent color, it will actually have the element of Transparency. You'll be able to see what's behind a control.

If you look below on the preview, you'll see the **100% Transparency** texts. Usually, they would be covered with the **color of the button parent (e.g. Panel/Form color)**, but with WiLBiT, we don't let it slide!

Scroll down to see a visual **Transparency example**.

### WiLBiT Preview

![image](https://user-images.githubusercontent.com/84229419/204539062-3e13e113-f6b9-4c2a-8cc6-8c09c45dbdfd.png)

### Transparency example

![image](https://user-images.githubusercontent.com/84229419/204552105-9b1c9473-db9a-40b4-bd48-a9b25e00f2bf.png)

WiLBiT is also **optimized for good performance, good UI loading**. What does that mean? When opening/using an application that operates with the WiLBiT Framework, performance should not be an issue, neither should UI loading.

However for **no flicker loading**, it's recommended to use the code below in your `Form.cs` file:

(C#)
```cs
private Rectangle sizeGripRectangle;
int paintReps = 0;

protected override void OnPaint(PaintEventArgs e)
{

    base.OnPaint(e);
    ControlPaint.DrawSizeGrip(e.Graphics, Color.Transparent, sizeGripRectangle);
    System.Threading.Thread.Sleep(0);

    if (paintReps++ % 500 == 0)
        Application.DoEvents();

}

protected override CreateParams CreateParams
{
    get
    {
        CreateParams cp = base.CreateParams;
        cp.ExStyle |= 0x02000000;

        return cp;
     }
}
```

(VB)
```vb
Private sizeGripRectangle As Rectangle
Private paintReps As Integer = 0

Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)
     MyBase.OnPaint(e)
     ControlPaint.DrawSizeGrip(e.Graphics, Color.Transparent, sizeGripRectangle)
     System.Threading.Thread.Sleep(0)
     If Math.Min(System.Threading.Interlocked.Increment(paintReps), paintReps - 1) Mod 500 = 0 Then Application.DoEvents()
End Sub

Protected Overrides ReadOnly Property CreateParams As CreateParams
     Get
         Dim cp As CreateParams = MyBase.CreateParams
         cp.ExStyle = cp.ExStyle Or &H02000000
         Return cp
End Get
```

This should not flicker **WiLBiT controls**, but may change the performance of your application.

### Support
- [x] C#.NET (100%)
- [x] VB.NET (100%)
- [x] C++.NET (50%)

-> 100% : Fully supported, should have no irregular bugs.\
-> 50% : Not completely supported, but should function.

### Early development

Not many features, not many updates. It's just me working on this, so I won't be able to work on it very quickly.

## Licensing
No license? No rights.\
You're only allowed to use the **distributed DLLs** from WiLBiT via **NuGET** or our [**Releases page**](https://github.com/Pronner/WiLBiT/releases), and if you use them immorally, you know what may be coming.
