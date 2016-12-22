---
title: "Miscellaneous Data Types (Visual Basic) | Microsoft Docs"
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
  - "Object data type, data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Miscellaneous Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供幾種非數字或字元導向的資料型別。  而這些型別是用來處理特定資料，例如是\/否值、日期\/時間值和物件位址。  
  
 如需 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料型別的並存比較表，請參閱[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## Boolean 型別  
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) 是解譯為 `True` 或 `False` 的不帶正負號值。  它的資料寬度取決於實作平台。  如果變數只能包含兩種狀態的值，例如 true\/false、是\/否或開\/關，則請宣告為 `Boolean`。  
  
## Date 型別  
 [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) 是 64 位元值，同時包含日期和時間資訊。  每遞增一次代表自公元 \(Gregorian calendar\) 1 年 1 月 1 日開始 \(12:00 AM\) 又經過了 100 奈秒 \(Nanosecond\)。  如果變數可以包含日期值、時間值或這兩者，則請宣告為 `Date`。  
  
## 物件型別  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)是 32 位元位址，用來指向您應用程式或某些其他應用程式中的物件執行個體。  `Object` 變數可以參考任何您應用程式可以辨認的物件，或是任何資料型別的資料。  這包含了*實值型別*，例如`Integer`， `Boolean`，和結構的執行個體，並*參考型別*、 哪些情況下，例如從類別建立物件的`String`和<xref:System.Windows.Forms.Form>，和陣列執行個體。  
  
 如果變數是儲存在編譯時期無法得知的類別執行個體指標，或是可以指向各種資料型別的資料，則請宣告為 `Object`。  
  
 利用`Object`資料型別時您可以使用它來儲存任何資料型別的資料。  而缺點在於，會進行佔用許多執行時間的額外運算，並減緩應用程式執行。  若使用實值型別的 `Object` 變數，則會發生 *Boxing* 和 *Unboxing*。  若用於參考型別，會發生「*晚期繫結*」\(Late Binding\)。  
  
## 請參閱  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)