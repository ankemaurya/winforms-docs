---
title: Canvas Resize
page_title: Canvas Resize
description: Canvas Resize
slug: radimageeditor-canvas-resize
tags: image, editor, resize 
published: True
position: 1
---


# Canvas Resize via UI

You can use the __Canvas Resize__ button which will open the canvas resize dialog. In the dialog you can set the alignment, the size, and the BackColor.

![](images/image-editor-canvas-resize001.png)
![](images/image-editor-canvas-resize002.png)

# Canvas Resize Programmatically

The following snippet shows how you can use the __ResizeCanvas__ method. You will need to specify the size, the alignment, and the BackColor.

#### Use the ResizeCanvas method

{{source=..\SamplesCS\ImageEditor\ImageEditorFeatures.cs region=Resize}} 
{{source=..\SamplesVB\ImageEditor\ImageEditorFeatures.vb region=Resize}}
````C#
radImageEditor1.ImageEditorElement.Resize(500, 500);

````
````VB.NET
radImageEditor1.ImageEditorElement.Resize(500, 500)

```` 


{{endregion}}

# See Also

* [Getting Started]({%slug radimageeditor-getting-started%})
* [Structure]({%slug radimageeditor-structure%})
* [Properties and Events]({%slug radimageeditor-properties-and-events%})