---
title: Selecting Dates
page_title: Selecting Dates
description: Selecting Dates
slug: calendar-customizing-behavior-selecting-dates
tags: selecting,dates
published: True
position: 5
---

# Selecting Dates



To enable selection of dates set the RadCalendar __AllowSelect__property to true. Set __AllowMultipleSelect__to true to enable more than one selection at one time.

## Selecting using the keyboard

See [Keyboard Navigation]({%slug calendar-customizing-behavior-keyboard-navigation%}) for a complete list of keys used to navigate RadCalendar.

## Selecting using the mouse

Select a single date by clicking on it.  If __AllowMultipleSelect__ is true, you can select multiple dates by holding the Ctrl key and clicking each date.

See the [Column and Row Headers]({%slug calendar-customizing-behavior-column-and-row-headers%}) topic for how to select entire columns and rows at one time.

## Selecting using the API

To select a single calendar day assign __RadCalendar SelectedDate__ a __DateTime__ value. To select multiple dates use the RadCalendar __SelectedDates.Add()__ method to add __DateTime__ values to the collection. To have more than one date in the __SelectedDates__ collection you should set the RadCalendar __AllowMultipleSelect__ property to true. The code snippet below shows how to select multiple date through the API.

#### __[C#] Selecting dates__

{{region selectingDates}}
	            radCalendar1.AllowMultipleSelect = true;
	            radCalendar1.SelectedDates.Add(new DateTime(2006, 10, 20, 0, 0, 0, 0));
	            radCalendar1.SelectedDates.Add(new DateTime(2006, 10, 19, 0, 0, 0, 0));
	            radCalendar1.SelectedDates.Add(new DateTime(2006, 10, 18, 0, 0, 0, 0));
	{{endregion}}



#### __[VB.NET] Selecting dates__

{{region selectingDates}}
	        RadCalendar1.AllowMultipleSelect = True
	        RadCalendar1.SelectedDates.Add(New DateTime(2006, 10, 20, 0, 0, 0, 0))
	        RadCalendar1.SelectedDates.Add(New DateTime(2006, 10, 19, 0, 0, 0, 0))
	        RadCalendar1.SelectedDates.Add(New DateTime(2006, 10, 18, 0, 0, 0, 0))
	{{endregion}}



You may also use the SelectedDates.AddRange() method to add an array of DateTime values: 

#### __[C#] Using SelectedDates.AddRange()__

{{region usingAddRange}}
	            radCalendar1.SelectedDate = new System.DateTime(2007, 9, 17, 0, 0, 0, 0);
	            radCalendar1.SelectedDates.AddRange(new DateTime[] { new DateTime(2007, 9, 17, 0, 0, 0, 0) });
	{{endregion}}



#### __[VB.NET] Using SelectedDates.AddRange()__

{{region usingAddRange}}
	        RadCalendar1.SelectedDate = New Date(2007, 9, 17, 0, 0, 0, 0)
	        RadCalendar1.SelectedDates.AddRange(New Date() {New Date(2007, 9, 17, 0, 0, 0, 0)})
	{{endregion}}

