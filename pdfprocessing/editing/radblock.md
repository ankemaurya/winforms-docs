---
title: Block
page_title: Block
description: Block
slug: radpdfprocessing-editing-block
tags: block
published: True
position: 1
---

# Block



__Block__ is a utility class that is intended to arrange the elements added to it in a flow-like manner. It can be used for measuring,
        drawing, and splitting of __FixedContentElements__.
      

## Add and Modify Content

The most common usage of __Block__ is to draw flowing content. Similarly to [FixedContentEditor]({%slug pdfprocessing-editing-fixedcontenteditor%}), 
          a block can contains images, graphics or text. The same Block instance can only be drawn once.
        

### Inserting Text

Inserting [TextFragments]({%slug pdfprocessing-model-textfragment%}) is achieved with one of the overloads of the
              __Insert()__ method.
              __Example 1__ show a simple insert by passing a string to the method.
            

#### __[C#] Example 1: Insert Text__

{{region radpdfprocessing-editing-block_0}}
	            Block block = new Block();
	            block.InsertText("Text");
	{{endregion}}



#### __[VB.NET] Example 1: Insert Text__

{{region radpdfprocessing-editing-block_0}}
	            Dim block As New Block()
	            block.InsertText("Text")
	            '#End Region
	
	            '#Region "radpdfprocessing-editing-block_1"
	            block.InsertText(New System.Windows.Media.FontFamily("Arial"), "Text")
	            '#End Region
	
	            '#Region "radpdfprocessing-editing-block_2"
	            'block.InsertText(fontFamily, fontStyle, fontWeight, "Text");
	            '#End Region
	        End Sub
	
	        Private Sub InsertLineBreak(block As Block)
	            '#Region "radpdfprocessing-editing-block_3"
	            block.InsertLineBreak()
	            '#End Region
	        End Sub
	
	        Private Sub DrawBlock(block As Block, fixedContentEditor As FixedContentEditor)
	            '#Region "radpdfprocessing-editing-block_4"
	            Dim boundingRect As New System.Windows.Rect(New System.Windows.Point(0, 0), New System.Windows.Size(200, 300))
	            block.Draw(fixedContentEditor, boundingRect)
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlock()
	            '#Region "radpdfprocessing-editing-block_5"
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure()
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlockSpecificSize()
	            '#Region "radpdfprocessing-editing-block_6"
	            Dim helloBlock As New Block()
	            helloBlock.InsertText("Hello")
	            Dim helloSize As System.Windows.Size = helloBlock.Measure()
	
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure(helloSize)
	            Dim secondBlock As Block = block.Split()
	            '#End Region
	        End Sub
	    End Class



__Example 2__ demonstrates how to insert text with a specific font family.
            

#### __[C#] Example 2: Insert Text with Arial FontFamily__

{{region radpdfprocessing-editing-block_1}}
	            block.InsertText(new System.Windows.Media.FontFamily("Arial"), "Text");
	{{endregion}}



#### __[VB.NET] Example 2: Insert Text with Arial FontFamily__

{{region radpdfprocessing-editing-block_1}}
	            block.InsertText(New System.Windows.Media.FontFamily("Arial"), "Text")
	            '#End Region
	
	            '#Region "radpdfprocessing-editing-block_2"
	            'block.InsertText(fontFamily, fontStyle, fontWeight, "Text");
	            '#End Region
	        End Sub
	
	        Private Sub InsertLineBreak(block As Block)
	            '#Region "radpdfprocessing-editing-block_3"
	            block.InsertLineBreak()
	            '#End Region
	        End Sub
	
	        Private Sub DrawBlock(block As Block, fixedContentEditor As FixedContentEditor)
	            '#Region "radpdfprocessing-editing-block_4"
	            Dim boundingRect As New System.Windows.Rect(New System.Windows.Point(0, 0), New System.Windows.Size(200, 300))
	            block.Draw(fixedContentEditor, boundingRect)
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlock()
	            '#Region "radpdfprocessing-editing-block_5"
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure()
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlockSpecificSize()
	            '#Region "radpdfprocessing-editing-block_6"
	            Dim helloBlock As New Block()
	            helloBlock.InsertText("Hello")
	            Dim helloSize As System.Windows.Size = helloBlock.Measure()
	
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure(helloSize)
	            Dim secondBlock As Block = block.Split()
	            '#End Region
	        End Sub
	    End Class



### Inserting Line Break

Inserting a line break results in the next element starting on a new line. The action is achieved with the __InsertLineBreak()__ method
              as shown in __Example 3__.
            

#### __[C#] Example 3: Break the Line__

{{region radpdfprocessing-editing-block_3}}
	            block.InsertLineBreak();
	{{endregion}}



#### __[VB.NET] Example 3: Break the Line__

{{region radpdfprocessing-editing-block_3}}
	            block.InsertLineBreak()
	            '#End Region
	        End Sub
	
	        Private Sub DrawBlock(block As Block, fixedContentEditor As FixedContentEditor)
	            '#Region "radpdfprocessing-editing-block_4"
	            Dim boundingRect As New System.Windows.Rect(New System.Windows.Point(0, 0), New System.Windows.Size(200, 300))
	            block.Draw(fixedContentEditor, boundingRect)
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlock()
	            '#Region "radpdfprocessing-editing-block_5"
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure()
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlockSpecificSize()
	            '#Region "radpdfprocessing-editing-block_6"
	            Dim helloBlock As New Block()
	            helloBlock.InsertText("Hello")
	            Dim helloSize As System.Windows.Size = helloBlock.Measure()
	
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure(helloSize)
	            Dim secondBlock As Block = block.Split()
	            '#End Region
	        End Sub
	    End Class



### Inserting Image

__Block__ provides the following methods for inserting images:
            

* block.InsertImage(imageSource);
                

* block.InsertImage(stream);
                

* block.InsertImage(imageSource, size);
                

* block.InsertImage(stream, size);
                

* block.InsertImage(imageSource, width, height);
                

* block.InsertImage(stream, width, height);
                

Information on images in the context of the library is available in the [ImageSource]({%slug pdfprocessing-model-imagesource%}) and
              [Image]({%slug pdfprocessing-model-image%}) articles.
            

### Inserting Geometries

[Geometries]({%slug pdfprocessing-concepts-geometry%}) allow you to describe 2D shapes in a document. The following
              methods can be used to insert different geometries.
            

* block.InsertCircle(center, radius);
                

* block.InsertEllipse(center, radiusX, radiusY);
                

* block.InsertLine(point1, point2);
                

* block.InsertPath(geometry);
                

* block.InsertRectangle(rectangle);
                

### Changing Current Styles

The __Block__ class has some properties and methods that affect how it will be rendered:
            

* __SpacingBefore:__ Represent the spacing before.
                

* __SpacingAfter:__ Represents the spacing after.
                

* __LineSpacing:__ The spacing between the lines.
                

* __LineSpacingType:__ specifies how to interpret the line spacing.
                

* __FirstLineIndent:__ The indent for the first line.
                

* __LeftIndent:__ The left indent.
                

* __RightIndent:__ The right indent.
                

* __BackgroundColor:__ The background color.
                

* __HorizontalAlignment:__ The horizontal alignment of the content.
                

* __VerticalAlignment:__ The vertical alignment of the content.
                

* __Bullet__ – The element that should be rendered as Block’s list bullet.
                

* __IndentAfterBullet__ – The indent size after the bullet element.
                

* __TextProperties__ and __GraphicProperties__ Responsible for text and graphic properties.
                  For more information see the [Text and Graphic Properties]({%slug pdfprocessing-editing-text-and-graphic-properties%}) article.
                

* __SaveTextProperties():__ Saves the TextProperties. It returns an IDisposable object which when disposed calls
                  __RestoreTextProperties()__ and can be used in using statement.
                

* __RestoreTextProperties():__ Restores the TextProperties to their previous state.
                

* __SaveGraphicProperties():__ Saves the GraphicProperties. It returns an IDisposable object which when disposed
                  calls __RestoreTextProperties()__ and can be used in using statement.
                

* __RestoreGraphicProperties():__ Restores the GrahpicPropertie to their previous state.
                

* __SaveProperties():__ Saves both text and graphic properties. It returns an IDisposable object which when disposed
                  calls __RestoreTextProperties()__ and can be used in using statement.
                

* __RestoreProperties():__ Restores both text and graphic properties.
                

* __SetBullet(List list, int listLevel):__ This method helps you to easily set bullet related properties respecting the 
                  numbering and the formatting of some List class instance. More information about lists you may 
                  find in [this article]({%slug radpdfprocessing-editing-list%})

* __Clear():__ Clears all elements in the block.
                

## Drawing a Block

A Block can be drawn to the content using the __Draw()__ method. The method accepts as a parameter a __Rectangle__,
          specifying the desired size and position relatively to the editor of the element.
        

__Example 4__ demonstrates how to draw a block.
        

#### __[C#] Example 4: Draw Block__

{{region radpdfprocessing-editing-block_4}}
	            System.Windows.Rect boundingRect = new System.Windows.Rect(new System.Windows.Point(0, 0), new System.Windows.Size(200, 300));
	            block.Draw(fixedContentEditor, boundingRect);
	{{endregion}}



#### __[VB.NET] Example 4: Draw Block__

{{region radpdfprocessing-editing-block_4}}
	            Dim boundingRect As New System.Windows.Rect(New System.Windows.Point(0, 0), New System.Windows.Size(200, 300))
	            block.Draw(fixedContentEditor, boundingRect)
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlock()
	            '#Region "radpdfprocessing-editing-block_5"
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure()
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlockSpecificSize()
	            '#Region "radpdfprocessing-editing-block_6"
	            Dim helloBlock As New Block()
	            helloBlock.InsertText("Hello")
	            Dim helloSize As System.Windows.Size = helloBlock.Measure()
	
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure(helloSize)
	            Dim secondBlock As Block = block.Split()
	            '#End Region
	        End Sub
	    End Class



>importantEvery block can be drawn only once. Otherwise an exception will be thrown.
          

## Measure Block Size

Measuring a Block can be achieved with one of the overloads of the __Measure()__ methods. Invoking the method without a 
          parameter will return the desired size of the elements in the block and set the block's __DesiredSize__ property. 
          The method is handy when you want to determine the size of the Block.
        

Calling the overload accepting available size measures the block in that specific size. Additionally to setting the __DesiredSize__ property,
          it sets the __PendingElements__ property with a collection of the elements that could not fit in the available size.
        

__Example 5__ creates a Block with text "Hello RadPdfProcessing!" and measures it.
        

#### __[C#] Example 5: Measure Block__

{{region radpdfprocessing-editing-block_5}}
	            Block block = new Block();
	            block.InsertText("Hello RadPdfProcessing!");
	            System.Windows.Size size = block.Measure();
	{{endregion}}



#### __[VB.NET] Example 5: Measure Block__

{{region radpdfprocessing-editing-block_5}}
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure()
	            '#End Region
	        End Sub
	
	        Private Sub MeasureBlockSpecificSize()
	            '#Region "radpdfprocessing-editing-block_6"
	            Dim helloBlock As New Block()
	            helloBlock.InsertText("Hello")
	            Dim helloSize As System.Windows.Size = helloBlock.Measure()
	
	            Dim block As New Block()
	            block.InsertText("Hello RadPdfProcessing!")
	            Dim size As System.Windows.Size = block.Measure(helloSize)
	            Dim secondBlock As Block = block.Split()
	            '#End Region
	        End Sub
	    End Class



## Split a Block

The __Split()__ method of a Block returns a new Block with the same properties. The resulting block contains all pending elements that
          do not fit in the current block, based on the result of the last measure call.
        

The code in __Example 6__ splits a block in two. The first will contains text "Hello" and the second – "RadPdfProcessing!".
        

# See Also

 * [Block]({%slug radpdfprocessing-editing-block%})

 * [TextFragment]({%slug pdfprocessing-model-textfragment%})

 * [Image]({%slug pdfprocessing-model-image%})

 * [Geometry]({%slug pdfprocessing-concepts-geometry%})

 * [Text and Graphic Properties]({%slug pdfprocessing-editing-text-and-graphic-properties%})