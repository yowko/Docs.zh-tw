---
title: "How to: Declare a Structure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations, structures"
  - "structure statements"
  - "statements [Visual Basic], structure"
  - "structures, declaring"
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare a Structure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以利用 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) 來開始結構的宣告，並利用 `End` `Structure` 陳述式結束宣告。  在兩陳述式之間至少要宣告一個「*項目*」\(Element\)。  雖然項目可以是任何資料型別，但是至少要有一個項目是非共用變數或非共用的非自訂事件。  
  
 您無法在結構宣告中初始化任何結構項目。  當您將變數宣告為結構型別時，藉由透過變數存取項目就能將值指派給項目。  
  
 如需結構和類別 \(Class\) 之間差異的詳細討論，請參閱 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 為了便於示範，假設您想要記錄員工的姓名、電話分機和薪水。  使用結構，您只要利用單一變數就可以達到這個目的。  
  
### 宣告結構  
  
1.  建立結構的開始陳述式和結束陳述式。  
  
     您可以使用 [Public](../../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 或 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字來指定結構的存取層級，或是保留預設值 `Public`。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  將項目加入至結構的主體。  
  
     結構至少要有一個項目。  您必須宣告每個項目並指定其存取層級。  如果您使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 而無任何關鍵字，存取範圍則預設值為 `Public`。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     上述範例中的 `salary` 欄位是 `Private`，這表示這個欄位無法從結構之外的地方存取，即使是從內含類別也一樣。  不過，`giveRaise` 程序是 `Public`，所以它可以從結構之外的地方呼叫。  同樣地，您可以從結構之外的地方引發 `salaryReviewTime` 事件。  
  
     除了變數、`Sub` 程序和事件以外，您還可以在結構中定義常數、`Function` 程序和屬性。  您最多只能將一個屬性指定為「*預設屬性*」\(Default Property\)，前提是它至少要取得一個引數。  您可以使用 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` 程序來處理事件。  如需詳細資訊，請參閱 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [User\-Defined Data Type](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)