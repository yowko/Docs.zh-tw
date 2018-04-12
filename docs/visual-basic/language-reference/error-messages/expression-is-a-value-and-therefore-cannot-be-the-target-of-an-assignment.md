---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>運算式是一個數值，不可以是指派的目標
陳述式嘗試將值指派給運算式。 您只能指派給值的可寫入變數、 屬性或陣列元素執行階段。 下列範例說明會發生此錯誤。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 類似的範例可以套用至屬性和陣列項目。  
  
 **間接存取。** 透過實值類型的間接存取也可以產生這個錯誤。 請考慮下列程式碼範例中，會嘗試設定的值<xref:System.Drawing.Point>藉由存取間接透過<xref:System.Windows.Forms.Control.Location%2A>。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 前述範例中的最後一個陳述式會失敗，因為它會建立暫存配置的<xref:System.Drawing.Point>所傳回的結構<xref:System.Windows.Forms.Control.Location%2A>屬性。 結構是實值類型，且陳述式執行後，不會保留暫時性結構。 藉由宣告和使用的變數未解決此問題<xref:System.Windows.Forms.Control.Location%2A>，這樣就可以建立更具永久性配置<xref:System.Drawing.Point>結構。 下列範例會顯示可以取代前述範例中的最後一個陳述式的程式碼。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **錯誤 ID:** BC30068  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果陳述式指派值的運算式，運算式以取代單一可寫入的變數、 屬性或陣列元素。  
  
-   如果此陳述式間接存取透過實值類型 （通常是結構），建立實值類型的變數。  
  
-   將適當的結構 （或其他實值型別） 指派給變數。  
  
-   您可以使用變數來存取要指派其值的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
