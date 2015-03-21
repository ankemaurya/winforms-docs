---
title: Localizing Scheduler Navigator
page_title: Localizing Scheduler Navigator
description: Localizing Scheduler Navigator
slug: scheduler-localization-localizing-scheduler-navigator
tags: localizing,scheduler,navigator
published: True
position: 1
---

# Localizing Scheduler Navigator



## 

The __RadSchedulerNavigator__ control uses the __SchedulerNavigatorLocalizationProvider__ class to define the default
          values for all strings that are displayed to the user.  You can easily override the default localization by inheriting from the
          __SchedulerNavigatorLocalizationProvider__ class and override its __GetLocalizedString__ method: 
        

#### __[C#]__

{{region navigatorProvider}}
	    public class CustomSchedulerNavigatorLocalizationProvider : SchedulerNavigatorLocalizationProvider
	    {
	        public override string GetLocalizedString(string id)
	        {
	            switch (id)
	            {
	                case SchedulerNavigatorStringId.DayViewButtonCaption:
	                    {
	                        return "Day View";
	                    }
	                case SchedulerNavigatorStringId.WeekViewButtonCaption:
	                    {
	                        return "Week View";
	                    }
	                case SchedulerNavigatorStringId.MonthViewButtonCaption:
	                    {
	                        return "Month View";
	                    }
	                case SchedulerNavigatorStringId.TimelineViewButtonCaption:
	                    {
	                        return "Timeline View";
	                    }
	                case SchedulerNavigatorStringId.ShowWeekendCheckboxCaption:
	                    {
	                        return "Show Weekend";
	                    }
	                case SchedulerNavigatorStringId.TodayButtonCaptionToday:
	                    {
	                        return "Today";
	                    }
	                case SchedulerNavigatorStringId.TodayButtonCaptionThisWeek:
	                    {
	                        return "This week";
	                    }
	                case SchedulerNavigatorStringId.TodayButtonCaptionThisMonth:
	                    {
	                        return "This month";
	                    }
	            }
	
	            return String.Empty;
	        }
	    }
	{{endregion}}



#### __[VB.NET]__

{{region navigatorProvider}}
	Public Class CustomSchedulerNavigatorLocalizationProvider
	    Inherits SchedulerNavigatorLocalizationProvider
	    Public Overrides Function GetLocalizedString(ByVal id As String) As String
	        Select Case id
	            Case SchedulerNavigatorStringId.DayViewButtonCaption
	                Return "Day View"
	            Case SchedulerNavigatorStringId.WeekViewButtonCaption
	                Return "Week View"
	            Case SchedulerNavigatorStringId.MonthViewButtonCaption
	                Return "Month View"
	            Case SchedulerNavigatorStringId.TimelineViewButtonCaption
	                Return "Timeline View"
	            Case SchedulerNavigatorStringId.ShowWeekendCheckboxCaption
	                Return "Show Weekend"
	            Case SchedulerNavigatorStringId.TodayButtonCaptionToday
	                Return "Today"
	            Case SchedulerNavigatorStringId.TodayButtonCaptionThisWeek
	                Return "This week"
	            Case SchedulerNavigatorStringId.TodayButtonCaptionThisMonth
	                Return "This month"
	        End Select
	
	        Return String.Empty
	    End Function
	End Class
	'#End Region



In order to utilize the new Localization Provider, you should create an instance of the new provider and assign it to the static
          __CurrentProvider__ property of __SchedulerNavigatorLocalizationProvider__ class:
        

#### __[C#]__

{{region assignNavigatorProvider}}
	            SchedulerNavigatorLocalizationProvider.CurrentProvider = new CustomSchedulerNavigatorLocalizationProvider();
	{{endregion}}



#### __[VB.NET]__

{{region assignNavigatorProvider}}
	        SchedulerNavigatorLocalizationProvider.CurrentProvider = New CustomSchedulerNavigatorLocalizationProvider()
	        '#End Region
	    End Sub
	
	End Class

