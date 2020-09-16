---
layout: post
title: Select multiple items from a list in Excel
date: 2016-11-27 14:21:55.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Excel
tags: []
meta:
  _edit_last: '1'
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: ''
  _jetpack_related_posts_cache: a:1:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1526314927;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:54;}i:1;a:1:{s:2:"id";i:5;}i:2;a:1:{s:2:"id";i:211;}}}}
  _wpas_done_all: '1'
  _jetpack_dont_email_post_to_subs: '1'
  dsq_thread_id: '5531807060'
author:

permalink: "/select-multiple-items-list-excel/"
---
For the rare occasion when you need to select multiple items from a list in Excel, the below VBA code will do the trick, complete with a nice selector panel. See the screen capture below for it in action.

![multiple-selector-excel]({{ site.baseurl }}/assets/images/2016/11/multiple-selector-excel-1.gif)

This first code snippet should be placed in the worksheet where the multiple selection is needed. Replace the range with the range of cells in&nbsp;which the selection takes place (ie. clicking on any cell Q12 to Q30 will trigger the selector panel).

```
Private Sub Worksheet\_SelectionChange(ByVal Target As Range) If Target.Count = 1 Then 'Range of cells to have the pop-up userform If Not Intersect(Range("Q12:Q30"), Target) Is Nothing Then UserForm1.Show End If End If End Sub
```

Next, create a new blank user form and add the below. Replace the range with the range of cells that contains the list of options that can be selected.

```
Private Sub UserForm\_Initialize() With ListBox1 .MultiSelect = fmMultiSelectMulti .ListStyle = fmListStyleOption plist = Sheets("source ws").Range("A23:A100") //replace the range here 'Filter Blanks For i = LBound(plist) To UBound(plist) If plist(i, 1) \<\> "" Then .AddItem Trim(plist(i, 1)) Next i End With End Sub Private Sub UserForm\_Activate() 'Match Listbox selections with ActiveCell selections Dim strCell As String, i As Long strCell = ActiveCell.Value & MySeperator With ListBox1 For i = 0 To .ListCount - 1 .Selected(i) = InStr(1, strCell, .List(i), 1) Next i End With UserForm1.Caption = "Select Projects" CommandButton1.Caption = "OK" End Sub Private Sub UserForm\_QueryClose(Cancel As Integer, CloseMode As Integer) 'Hide userform if Close "X" clicked If CloseMode = 0 Then Cancel = True Me.Hide End If End Sub Private Sub CommandButton1\_Click() Dim i As Long, strTemp As String With ListBox1 'Read selections For i = 0 To .ListCount - 1 If .Selected(i) Then strTemp = strTemp & .List(i) & "," .Selected(i) = False ' Clear selections End If Next i End With If Len(strTemp) Then strTemp = Left(strTemp, Len(strTemp) - Len(MySeperator)) ActiveCell.Value = strTemp Else ActiveCell.ClearContents ActiveCell.Value = "-- Select Project --" End If UserForm1.Hide End Sub
```

Unfortunately, there is no method to achieve this without the use of macros as of Excel 2016.

&nbsp;

&nbsp;

