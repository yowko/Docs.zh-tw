---
title: "How to: Declare Enumerations (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "declarations, enumerations"
  - "enumerations [Visual Basic], declaring"
  - "declaring enumerations"
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以在類別或模組的宣告區段中，以 `Enum` 陳述式 \(Statement\) 建立列舉型別 \(Enumeration\)。  您無法在方法中宣告列舉型別。  若要指定適當的存取層級，請使用 `Private`、`Protected`、`Friend` 或 `Public`。  
  
 `Enum` 型別具有一名稱、一基礎型別和一組欄位，各表示一個常數。  名稱必須為有效的 [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] 限定詞 \(Qualifier\)。  基礎型別必須是整數型別之一，也就是 `Byte`、`Short`、`Long` 或 `Integer`。  `Integer` 為預設值。  列舉都是強型別 \(Strongly Typed\)，無法與整數型別交換使用。  
  
 列舉不能有浮點數值。  如果使用 `Option Strict On` 將浮點值指派給列舉，就會產生編譯器錯誤。  如果 `Option Strict` 為 `Off`，該值將自動轉換成 `Enum` 型別。  
  
 如需名稱的詳細資訊，或想知道如何使用 `Imports` 陳述式來去除限定名稱的限制，請參閱[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### 若要宣告列舉型別  
  
1.  撰寫一宣告，其中包括如下列範例中之程式碼存取層次、`Enum` 關鍵字及有效名稱，各者分別宣告不同的 `Enum`。  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  定義列舉型別中的常數。  依預設，列舉型別的第一個常數會初始化為 `0`，之後的常數則會初始化成前一個常數值加上 1。  例如，下列的列舉型別 `Days` 包含名為 `Sunday` 的常數 \(其值為 `0`\)、名為 `Monday` 的常數 \(其值為 `1`\)、名為 `Tuesday` 的常數 \(其值為 `2`\)，依此類推。  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  您可以使用指派陳述式明確地指派列舉型別中常數的值。  您可以指定任何整數值，包含負數。  例如，您可能希望其值小於零的常數代表錯誤狀態。  在下列的列舉型別中，已明確指派常數 `Invalid` 之值為 `–1`，且指派常數 `Sunday` 之值為 `0`。  由於它是列舉型別中的第一個常數，`Saturday` 也已初始化為值 `0`。  `Monday` 的值為 `1` \(為 `Sunday` 的值加 1\)；`Tuesday` 的值為 `2`，依此類推。  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### 若要將列舉宣告為明確型別  
  
-   使用 `As` 子句指定列舉的型別，如下列範例所示。  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## 請參閱  
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../Topic/How%20to:%20Determine%20the%20String%20Associated%20with%20an%20Enumeration%20Value%20\(Visual%20Basic\).md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)