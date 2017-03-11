---
title: "Composite Data Types (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "classes [Visual Basic], composite types"
  - "types [Visual Basic], composite"
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Composite Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

除了 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供的基本資料型別之外，也可以組合不同型別的項目來建立「*複合資料型別*」\(Composite Data Type\)，例如結構、陣列及類別。  您可以從基本型別以及其他複合型別來建立複合資料型別。  例如，您可以定義結構元素的陣列或是具有陣列成員的結構。  
  
## 資料型別  
 複合型別與其元件的任何資料型別都不同。  例如，`Integer` 元素的陣列並不屬於 `Integer` 資料型別。  
  
 陣列資料型別通常會視需要，使用元素型別、括號和逗號來表示。  例如，`String` 元素的一維陣列會表示成 `String()`，而 `Boolean` 元素的二維陣列會表示成 `Boolean(,)`。  
  
## 結構型別  
 沒有任何單一的資料型別可包含所有的結構。  相反地，結構的每個定義都代表唯一的資料型別，即使兩個結構以相同的順序定義相同的項目。  然而，如果您建立兩個或兩個以上相同結構的執行個體，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將它們視為相同的資料型別。  
  
## 陣列型別  
 沒有任何單一的資料型別可包含所有的陣列。  陣列中特定執行個體的資料型別是由以下來決定：  
  
-   屬於陣列的事實  
  
-   陣列的陣序 \(維度數目\)  
  
-   陣列的元素型別  
  
 尤其要注意的是，指定維度 \(Dimension\) 的長度並不屬於執行個體的資料型別。  下列範例將說明這點。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在前述範例中，雖然陣列變數 `arrayA` 和 `arrayB` 初始化為不同的長度，但還是將它們視為屬於相同的資料型別 `Byte()`。  變數 `arrayB` 和 `arrayC` 由於其元素型別不同，而具有不同型別。  變數 `arrayC` 和 `arrayD` 由於其陣序不同，而具有不同型別。  變數 `arrayD` 和 `arrayE` 具有相同型別 `Short(,)`，因為其陣序和元素型別都相同，即使 `arrayD` 尚未初始化。  
  
 如需陣列的詳細資訊，請參閱 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## 類別型別  
 沒有任何單一的資料型別可包含所有的類別。  雖然類別可以繼承自另一個類別，但各自為獨立的資料型別。  相同類別的多個執行個體都屬於相同資料型別。  如果將某個類別執行個體變數指派給另一個，則它們不但會有相同的資料型別，也會指向記憶體中的相同類別執行個體。  
  
 如需類別的詳細資訊，請參閱 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Visual Basic 中的泛型類型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)