---
title: "無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords: BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2cf8a40060359393807cfb648c46fef9ed853af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位
匿名類型的一個屬性用來初始化匿名類型的另一個屬性時，編譯器不接受匿名轉換為運算式樹狀架構。 例如，在下列程式碼，`Prop1`初始設定清單中宣告，然後再使用的初始值為`Prop2`。  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **錯誤 ID:** BC36548  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將指定的初始值`Prop1`給區域變數。 將該變數指派給兩者`Prop1`和`Prop2`，如下列程式碼所示。  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [運算式樹狀結構](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [如何：使用運算式樹狀架構建置動態查詢](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
