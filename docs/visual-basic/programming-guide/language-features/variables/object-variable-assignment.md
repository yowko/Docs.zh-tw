---
title: "Object Variable Assignment (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Nothing keyword, object variable assignment"
  - "object variables, initializing"
  - "variables [Visual Basic], initializing"
  - "objects [Visual Basic], current instance"
  - "object variables, assigning"
  - "variables [Visual Basic], object variables"
  - "current instance, defined"
  - "variables [Visual Basic], assigning"
  - "assignment statements, object variable assignment"
  - "Me keyword, as object variable"
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Object Variable Assignment (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可使用一般的指派陳述式來指派物件給物件變數。  下列範例會說明如何指派物件運算式或 [Nothing](../../../../visual-basic/language-reference/nothing.md) 關鍵字。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` 表示目前沒有物件被指派至該變數。  
  
## 初始化  
 在程式碼開始執行時，物件變數會初始化為 `Nothing`。  執行宣告陳述式 \(Declaration Statement\) 時，包含初始化之宣告的物件變數會重新初始化為指定的值。  
  
 您可以使用 [New](../../../../visual-basic/language-reference/operators/new-operator.md) 關鍵字，在宣告中包含初始化。  下列宣告陳述式會宣告 `testUri` 和 `ver` 物件變數，並為它們指派特定的物件。  各宣告陳述式都會使用一個適當類別的多載建構函式，將物件初始化。  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## 結束關聯  
 將物件變數設定為 `Nothing` 會中止變數與任何特定物件的關聯。  這會避免您不小心更改變數而改變該物件。  這個動作也可以讓您測試物件變數是否指向有效的物件，如下列範例所示。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 如果您的變數所參考的物件位於另一個應用程式中，則這項測試無法判斷是該應用程式已結束或是只是該應用程式使物件失效。  
  
 具有 `Nothing` 值的物件變數也稱為「*Null 參考*」\(Null Reference\)。  
  
## 目前執行個體  
 物件的「*目前執行個體*」\(Current Instance\) 是程式碼目前正在其中執行的執行個體。  由於所有的程式碼都是在程序中執行，目前執行個體是程序被叫用 \(Invoke\) 的執行個體。  
  
 `Me` 關鍵字可以做為物件變數，參考目前執行個體。  如果程序不是 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)，它可以使用 `Me` 關鍵字取得目前執行個體的指標。  共用的程序無法與類別的特定執行個體產生關聯。  
  
 `Me` 的使用對於將目前執行個體傳遞至另一個模組中的程序特別有用。  例如，假設您有一些 XML 文件，並想要將一些標準文字加入全部的文件中。  下列範例定義了新增程序。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 每個 XML 文件物件就可以呼叫該程序，並將其目前的執行個體做為引數傳遞。  以下範例就是示範這項作業。  
  
```  
addStandardText(Me)  
```  
  
## 請參閱  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Make an Object Variable Not Refer to Any Instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)