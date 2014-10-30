###Todo
- [x] Implement Vertex Array support
- [x] Implement Shader support
- [x] Remove legacy OpenGL render code and switch to a fully programmable pipeline forward compatible with OpenGL 4.4
- [ ] Remove option to pass in a null Configuration object - this only adds to visual complexity
- [ ] Finish refactoring library


###Using Vertex Buffers
Initialize your vertex buffer
```C#
var config = new QFontBuilderConfiguration() 
{ 
  TextGenerationRenderHint = TextGenerationRenderHint.SystemDefault 
};

QFont qfont = new QFont(font, config);
```

Print to the vertex buffer
```C#
qfont.PrintToVBO("i love", new Vector3(0, 0, 0), Color.Red);
qfont.PrintToVBO("quickfont", new Vector3(0, 10, 0), Color.Blue);
```

When you've printed everything call Load 
```C#
qfont.LoadVBOs();
```

Then draw it
```C#
qfont.DrawVBOs();
```

Keep calling DrawVBOs() each frame.  When something needs to change, reset the VBO
```C#
qfont.ResetVBOs();
```

Then repeat the process: Print, Load Draw.