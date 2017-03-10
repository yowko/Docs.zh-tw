---
title: "How to: Create a New Variable (Visual Basic) | Microsoft Docs"
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
  - "Dim statement"
  - "variables [Visual Basic], creating"
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# How to: Create a New Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 建立變數。  
  
### 若要建立新變數  
  
1.  在 `Dim` 陳述式 \(Statement\) 中宣告變數。  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  包括變數特性的規格，例如 [Private](../../../../visual-basic/language-reference/modifiers/private.md)、[Static](../../../../visual-basic/language-reference/modifiers/static.md)、[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) 或 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。  如需詳細資訊，請參閱[Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     如果在宣告中使用其他關鍵字，則不需要 `Dim` 關鍵字。  
  
3.  在規格之後加上變數名稱，這需要遵守 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 規則和慣例。  如需詳細資訊，請參閱[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  在名稱之後加上 [As](../../../../visual-basic/language-reference/statements/as-clause.md) 子句，以指定變數的資料型別。  
  
    ```  
    Public Static newCustomer As Customer   
    ```  
  
     如果未指定資料型別，則預設為 `Object`。  
  
5.  在 `As` 子句之後加上等號 \(`=`\)，並在等號之後加上變數的初始值。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 在每次執行 `Dim` 陳述式時，都會將所指定的值指定給變數。  如果未指定初始值，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在第一次進入內含 `Dim` 陳述式的程式碼時，指定變數資料型別的預設初始值。  
  
     如果變數是參考型別，則可建立其類別的執行個體，方法是在 `As` 子句中併入 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) 關鍵字。  如果未使用 `New`，則變數的初始值為 [Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## 請參閱  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)