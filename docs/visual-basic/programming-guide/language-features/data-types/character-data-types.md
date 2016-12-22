---
title: "Character Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "data types [Visual Basic], character"
  - "String data type, character data types"
  - "character data types [Visual Basic]"
  - "Char data type, character data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Character Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供「*字元資料型別*」\(Character Data Type\) 來處理可列印及可顯示的字元。  雖然 `Char` 和 `String` 都可以處理 Unicode 字元，但前者只能存放單一字元，而後者可包含任何數目的字元。  
  
 如需 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料型別的並存比較表，請參閱[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## Char 型別  
 `Char` 資料型別是一個雙位元組 \(16 位元\) 的 Unicode 字元。  如果某個變數只會儲存正好一個的字元，則請宣告為 `Char`。  例如：  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 `Char` 或 `String` 變數中的每個可能值都是 Unicode 字元集的「*字碼指標*」\(Code Point\) 或字元碼。  Unicode 字元包括基本 ASCII 字元集、其他各種字母字元、重音、貨幣符號、分數、變音符號 \(Diacritic\) 和數學及技術符號。  
  
> [!NOTE]
>  Unicode 字元集保留「*Surrogate 字組*」\(Surrogate Pair\) 的字碼指標 D800 到 DFFF \(十進位數 55296 到 55551\)，此字組需要有兩個 16 位元的值來表示單一字碼指標。  `Char` 變數無法保留 Surrogate 字組，而 `String` 會使用兩個位置來保留這類字組。  
  
 如需詳細資訊，請參閱 [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## String 型別  
 `String` 資料型別是零個或多個雙位元組 \(16 位元\) 的 Unicode 字元組成的序列 \(Sequence\)。  如果某個變數可以包含任何數目的字元，則請宣告為 `String`。  例如：  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 如需詳細資訊，請參閱 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## 請參閱  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic 中的泛型類型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)