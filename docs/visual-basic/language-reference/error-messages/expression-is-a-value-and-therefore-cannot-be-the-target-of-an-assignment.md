---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826128"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>運算式是一個數值，不可以是指派的目標
陳述式會嘗試將值指派給運算式。 您只能指派給可寫入的變數、 屬性或陣列元素的值，在執行階段。 下列範例說明如何可能會發生此錯誤。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 類似的範例可以套用至屬性和陣列項目。  
  
 **間接存取。** 透過實值類型的間接存取也可以產生這個錯誤。 下列程式碼範例，嘗試設定的值，請考慮<xref:System.Drawing.Point>藉由存取間接透過<xref:System.Windows.Forms.Control.Location%2A>。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 前述範例中的最後一個陳述式會失敗，因為它會建立只有暫存的配置<xref:System.Drawing.Point>所傳回的結構<xref:System.Windows.Forms.Control.Location%2A>屬性。 結構是實值類型，並執行陳述式之後，不會保留暫時性結構。 未解決此問題，藉由宣告和使用的變數<xref:System.Windows.Forms.Control.Location%2A>，以建立更永久的配置<xref:System.Drawing.Point>結構。 下列範例顯示可以取代前述範例中的最後一個陳述式的程式碼。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **錯誤 ID:** BC30068  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果陳述式會將值指派給運算式，運算式以取代單一可寫入的變數、 屬性或陣列元素。  
  
-   如果此陳述式間接存取透過實值型別 （通常是結構），建立變數來保存實值型別。  
  
-   將適當的結構 （或其他實值型別） 指派給變數。  
  
-   您可以使用變數來存取屬性，以將它指派值。  
  
## <a name="see-also"></a>另請參閱

- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
