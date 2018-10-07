---
layout: page
title: "VBA Template"
tags: [template, sometag, some other tag, tcsobay]
---

```visualbasic
Public Sub KillFilter()

  Dim Counter As Integer

  On Error Go To Hell
  If ActiveSheet.AutoFilterMode Then
     ActiveSheet.AutoFilterMode = False
  End If

'<----- Abandon hope all ye who enter here ----->
Hell:
Counter = 0
Do While Counter < 100
  Debug.Print "you need to participate on one more unnecessary meeting"

End Sub
```
