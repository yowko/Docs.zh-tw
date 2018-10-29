---
title: 物件變數指派 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 571b09a0783ec0dfd09970b000faec39dca682b3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201934"
---
# <a name="object-variable-assignment-visual-basic"></a>物件變數指派 (Visual Basic)
您可以使用一般的指派陳述式來將物件指派給物件變數。 您可以指派物件運算式或[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，如下列範例說明。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` 表示沒有目前指派給變數的物件。  
  
## <a name="initialization"></a>初始化  
 當您的程式碼開始執行，您的物件變數會初始化為`Nothing`。 其宣告包含初始化這些都會重新初始化，為您指定的宣告陳述式執行時的值。  
  
 您也可以使用在宣告中包含初始化[新增](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字。 下列宣告陳述式宣告物件變數`testUri`和`ver`並為其指派特定的物件。 每個使用其中一個適當的類別的多載建構函式來初始化物件。  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>取消關聯  
 若要設定物件變數`Nothing`中止的執行中的變數與任何特定物件的關聯。 這會防止您不小心變更藉由變更變數的物件。 它也可讓您測試物件變數是否指向有效的物件，如下列範例所示。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 如果您的變數所參考的物件是在另一個應用程式中，這項測試無法判斷該應用程式是否已結束，或是只失效的物件。  
  
 物件變數的值`Nothing`也稱為*為 null 參考*。  
  
## <a name="current-instance"></a>目前的執行個體  
 *目前的執行個體*的物件是目前執行所在的程式碼。 因為所有的程式碼會執行程序內，目前的執行個體是在其中叫用程序。  
  
 `Me`關鍵字做為物件變數參考目前的執行個體。 如果不是程序[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)，它可以使用`Me`關鍵字來取得目前的執行個體的指標。 共用的程序不能與類別的特定執行個體相關聯。  
  
 使用`Me`特別適用於將目前的執行個體傳遞至另一個模組中的程序。 例如，假設您有幾個 XML 文件，而且想要它們全部加入一些標準的文字。 下列範例會定義要執行這項操作的程序。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 每個 XML 文件物件然後可以呼叫程序，並將其目前的執行個體傳遞做為引數。 下列範例為其示範。  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [如何： 宣告物件變數，並在 Visual Basic 中將物件指派給它](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [如何：讓物件變數不參考執行個體](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
