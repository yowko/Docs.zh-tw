---
title: "Structure Variables (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structures, variables"
  - "structures, structure variables"
  - "variables [Visual Basic], structure variables"
  - "structure variables"
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Structure Variables (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

一旦建立結構之後，您可以將程序層次及模組層次變數宣告為該型別。  例如，您可以建立一個結構，來記錄關於電腦系統的資訊。  以下範例就是示範這項作業。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 接著您可以宣告該型別的變數。  下面這個宣告可說明這點：  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  在類別 \(Class\) 及模組中，使用可進行公用存取的 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 預設值來宣告結構。  如果您希望結構是私用的，請確定使用 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字來宣告結構。  
  
## 存取結構值  
 若要指派並擷取結構變數元素的值，使用的方法與在物件上設定並取得屬性的語法相同。  您可以在結構變數名稱與項目名稱之間，放置成員存取運算子 \(Member Access Operator\) \(`.`\)。  下列範例會存取之前宣告為型別 `systemInfo` 的變數項目。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## 指派結構變數  
 若兩變數都屬於相同的結構型別，您也可以將一變數指派至另一變數。  這樣會將結構的所有項目都複製到另一個結構的對應項目。  下面這個宣告可說明這點：  
  
```  
yourSystem = mySystem  
```  
  
 如果結構元素是一個參考型別，例如 `String`、`Object` 或陣列，則會複製資料指標。  在前述範例中，如果 `systemInfo` 包含物件變數，則會將指標從 `mySystem` 複製到 `yourSystem`，並透過存取其他結構時可能生效的結構，來變更物件資料。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)