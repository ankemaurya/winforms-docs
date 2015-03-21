---
title: Localizattion
page_title: Localizattion
description: Localizattion
slug: forms-and-dialogs-colordialog-localization
tags: localizattion
published: True
position: 3
---

# Localizattion



## 

To localize RadColorDialog form to display text and messages in a specific language:

* All required classes for localization are defined in 
		  		__Telerik.WinControls.UI.Localization__ namespace.
		  	

* Start by creating a descendant of the __ColorDialogLocalizationProvider__ class.
		  	

* Override the __GetLocalizedString(string id)__ method and provide a
		  		translation for the label and user messages. If a translation is not provided, the default
		  		value will be returned. This behavior is guaranteed by the call to the base 
		  		__GetLocalizedString__ method in the __default__ 
		  		clause of the __switch__ statement in the example.
		  	

Below is a sample implementation of a custom localization provider, which returns translations of the default values:
		

#### __[C#] Localizing RadColorDialog strings__

{{region localization1}}
	        public class CustomColorDialogLocalizationProvider : ColorDialogLocalizationProvider
	        {
	            public override string GetLocalizedString(string id)
	            {
	                switch (id)
	                {
	                    //localizing the static strings
	                    case ColorDialogStringId.ColorDialogProfessionalTab: return "Localized Professional";
	                    case ColorDialogStringId.ColorDialogWebTab: return "Localized Web";
	                    case ColorDialogStringId.ColorDialogSystemTab: return "Localized System";
	                    case ColorDialogStringId.ColorDialogBasicTab: return "Localized Basic";
	                    case ColorDialogStringId.ColorDialogAddCustomColorButton: return "Localized Add Custom Color";
	                    case ColorDialogStringId.ColorDialogOKButton: return "Localized OK";
	                    case ColorDialogStringId.ColorDialogCancelButton: return "Localized Cancel";
	                    case ColorDialogStringId.ColorDialogNewColorLabel: return "Localized New";
	                    case ColorDialogStringId.ColorDialogCurrentColorLabel: return "Localized Current";
	                    case ColorDialogStringId.ColorDialogCaption: return "Localized Color dialog";
	                    //you can also localize the names of the colors
	                    case "Black": return "Localized Black";
	                    case "Blue": return "Localized Blue";
	                    case "Aqua": return "Localized Aqua";
	                }
	
	                return base.GetLocalizedString(id);
	            }
	        }
	{{endregion}}



#### __[VB.NET] Localizing RadColorDialog strings__

{{region localization1}}
	    Public Class CustomColorDialogLocalizationProvider
	        Inherits ColorDialogLocalizationProvider
	        Public Overrides Function GetLocalizedString(id As String) As String
	            Select Case id
	                'localizing the static strings
	                Case ColorDialogStringId.ColorDialogProfessionalTab
	                    Return "Localized Professional"
	                Case ColorDialogStringId.ColorDialogWebTab
	                    Return "Localized Web"
	                Case ColorDialogStringId.ColorDialogSystemTab
	                    Return "Localized System"
	                Case ColorDialogStringId.ColorDialogBasicTab
	                    Return "Localized Basic"
	                Case ColorDialogStringId.ColorDialogAddCustomColorButton
	                    Return "Localized Add Custom Color"
	                Case ColorDialogStringId.ColorDialogOKButton
	                    Return "Localized OK"
	                Case ColorDialogStringId.ColorDialogCancelButton
	                    Return "Localized Cancel"
	                Case ColorDialogStringId.ColorDialogNewColorLabel
	                    Return "Localized New"
	                Case ColorDialogStringId.ColorDialogCurrentColorLabel
	                    Return "Localized Current"
	                Case ColorDialogStringId.ColorDialogCaption
	                    Return "Localized Color dialog"
	                    'you can also localize the names of the colors
	                Case "Black"
	                    Return "Localized Black"
	                Case "Blue"
	                    Return "Localized Blue"
	                Case "Aqua"
	                    Return "Localized Aqua"
	            End Select
	
	            Return MyBase.GetLocalizedString(id)
	        End Function
	    End Class
	{{endregion}}



To apply the custom localization provider, instantiate and assign it to the current localization provider:
		

#### __[C#] Using the custom localization provider__

{{region localization2}}
	            ColorDialogLocalizationProvider.CurrentProvider = new CustomColorDialogLocalizationProvider();
	{{endregion}}



#### __[VB.NET] Using the custom localization provider__

{{region localization2}}
	        ColorDialogLocalizationProvider.CurrentProvider = New CustomColorDialogLocalizationProvider()
	{{endregion}}



The code provided above illustrates the approach to be used to localize the 
        	__RadColorDialog__ and is not intended as a full translation.
        