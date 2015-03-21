---
title: Watermark Dialog
page_title: Watermark Dialog
description: Watermark Dialog
slug: tpf-printing-support-radwatermarkdialog
tags: watermark,dialog
published: True
position: 2
---

# Watermark Dialog



## Watermark dialog

The watermark preview dialog allows the user to set up the watermark of the associated RadPrintDocument.
    		The dialog consist of one preview control, two groups of common settings and two pages with settings
    		for the text and image watermark settings. To use the Watermark preview dialog you have to create 
    		a new instance of the __WatermarkPreviewDialog__ by pass RadPrintDocument instance
    		to the constructor and call the __ShowDialog__ method:
    	

#### __[C#]__

{{region WaterMark}}
	            RadPrintDocument document = new RadPrintDocument();
	            document.AssociatedObject = this.radGridView1;
	
	            WatermarkPreviewDialog dialog = new WatermarkPreviewDialog(document);
	            dialog.ShowDialog();
	{{endregion}}



#### __[VB.NET]__

{{region WaterMark}}
	        Dim document As New RadPrintDocument()
	        document.AssociatedObject = Me.RadGridView1
	
	        Dim dialog As New WatermarkPreviewDialog(document)
	        dialog.ShowDialog()
	{{endregion}}



![tpf-printing-support-end-user-functionality-radprintpreviewdialog](images/tpf-printing-support-end-user-functionality-radprintpreviewdialog.png)

The available common settings are placed in the two group boxes on the bottom part of the dialog.
  			The position options determine whether the watermark will be drawn before the content of the page 
  			or over it. The second group determines the pages on which the watermark will be printed.
  		