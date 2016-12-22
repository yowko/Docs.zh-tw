---
title: "How to: Hold More Than One Value in a Variable (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "arrays [Visual Basic], compilation errors"
  - "types [Visual Basic], composite"
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Hold More Than One Value in a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果將變數宣告為「*複合資料型別*」\(Composite Data Type\)，則此變數會存放一個以上的值。  
  
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)包括結構、陣列和類別。  複合資料型別的變數可存放基礎資料型別 \(Elementary Data Type\) 和其他複合型別的組合。  結構和類別可以存放程式碼及資料。  
  
### 若要在變數中存放一個以上的值  
  
1.  決定想要用於變數的複合資料型別。  
  
2.  如果尚未定義複合資料型別，請先定義，以使變數能使用該資料型別。  
  
    -   使用 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) 定義結構。  
  
    -   使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 定義陣列。  
  
    -   使用 [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) 定義類別。  
  
3.  使用 `Dim` 陳述式 \(Statement\) 宣告變數。  
  
4.  在變數名稱之後加上 `As` 子句。  
  
5.  在 `As` 關鍵字之後加上適當的複合資料型別名稱。  
  
## 請參閱  
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Objects and Classes](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)