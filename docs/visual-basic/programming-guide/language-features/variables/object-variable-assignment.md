---
title: "物件變數指派 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-assignment-visual-basic"></a>物件變數指派 (Visual Basic)
您可以使用一般的指派陳述式來指派給物件變數的物件。 您可以指派物件運算式或[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，如下列範例說明。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing`表示沒有目前指派給變數的物件。  
  
## <a name="initialization"></a>初始化  
 當您的程式碼開始執行，您的物件變數初始化為`Nothing`。 重新初始化其宣告包含初始化這些宣告陳述式執行時，您指定的值。  
  
 您也可以使用在宣告中包含初始化[新增](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字。 下列宣告陳述式宣告物件變數`testUri`和`ver`並為其指派的特定物件。 使用其中一個適當的類別的多載建構函式以初始化物件。  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>取消關聯  
 若要設定物件變數`Nothing`停止與任何特定物件的變數關聯。 這可防止不小心變更物件變更的變數。 它也可讓您測試物件變數是否指向有效的物件，如下列範例所示。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 如果您的變數所參考的物件位於另一個應用程式，這項測試無法判斷該應用程式是否已結束，或是只失效的物件。  
  
 物件變數值是`Nothing`也稱為*null 參考*。  
  
## <a name="current-instance"></a>目前執行個體  
 *目前執行個體*的物件是在其中目前執行程式碼。 由於所有的程式碼會執行程序內，目前的執行個體是程序已叫用。  
  
 `Me`關鍵字做為物件變數參考目前的執行個體。 如果不是程序[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，它可以使用`Me`關鍵字來取得目前的執行個體的指標。 共用的程序不能與類別的特定執行個體相關聯。  
  
 使用`Me`將目前的執行個體傳遞至另一個模組中的程序特別有用。 例如，假設您的 XML 文件數目與要加入至所有端點的一些標準的文字。 下列範例會定義可執行此動作的程序。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 每個 XML 文件物件無法呼叫程序，然後將其目前的執行個體傳遞做為引數。 下列範例為其示範。  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [如何： 宣告物件變數，並在 Visual Basic 中為其指派物件](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [如何：讓物件變數不參考執行個體](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
