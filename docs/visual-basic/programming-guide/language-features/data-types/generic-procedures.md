---
title: "Generic Procedures in Visual Basic | Microsoft Docs"
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
  - "generic methods, type inference"
  - "generics [Visual Basic], type inference"
  - "procedures, generic"
  - "generic procedures"
  - "type inference, generics"
  - "generic methods"
  - "type inference"
  - "generics [Visual Basic], procedures"
  - "generic procedures, type inference"
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Generic Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*泛型程序*」\(Generic Procedure\)，亦稱為「*泛型方法*」\(Generic Method\)，是指至少使用一個型別參數定義的程序。  它可讓呼叫程式碼在每次呼叫程序時，根據需求調整資料型別。  
  
 如果某個程序只是在泛型類別或泛型結構內定義，則該程序不一定是泛型。  若要成為泛型，除了可能採用的一般參數以外，程序至少必須採用一個型別參數。  泛型類別或結構可能含有非泛型程序，而非泛型類別、結構或模組也可能含有泛型程序。  
  
 泛型程序可以在一般參數清單、傳回型別 \(如果有的話\) 和程序程式碼中使用自己的型別參數。  
  
## 型別推斷  
 您可以呼叫泛型程序，但不提供任何型別引數。  如果您用這種方式呼叫，編譯器 \(Compiler\) 就會嘗試判斷適當的資料型別，以傳遞至程序的型別引數。  這就稱為「*型別推斷*」\(Type Inference\)。  下列程式碼將示範一則呼叫，其中編譯器會推斷出它應該傳遞型別 `String` 至型別參數 `t`。  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 如果編譯器無法從呼叫的內容推斷型別引數，它就會回報錯誤。  發生這類錯誤的其中一個可能原因是陣列陣序不符。  例如，假設您將一般參數定義為型別參數的陣列。  如果您呼叫提供不同陣序 \(維度數目\) 之陣列的泛型程序，則此不符就會導致型別參考失敗。  下列程式碼將示範一則呼叫，其中二維陣列會傳遞至預期一維陣列的程序。  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 您可以只透過省略所有型別引數，叫用 \(Invoke\) 型別參考。  如果您提供一個型別引數，就必須提供所有引數。  
  
 只有泛型程序才支援型別參考。  您無法在泛型類別、結構、介面或委派 \(Delegate\) 上叫用型別參考。  
  
## 範例  
  
### 描述  
 下列範例會定義泛型 `Function` 程序，以便找出陣列中的特定元素。  它會定義一個型別參數並使用此參數在參數清單中建構兩個參數。  
  
### 程式碼  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### 註解  
 上述範例需要能夠根據 `searchArray` 的每個元素比較 `searchValue`。  為了確保這項能力，它會約束型別參數 `T` 必須實作 <xref:System.IComparable%601> 介面。  此程式碼會使用 <xref:System.IComparable%601.CompareTo%2A> 方法而非 `=` 運算子，因為無法保證提供給 `T` 的型別引數可支援 `=` 運算子。  
  
 您可以使用下列程式碼測試 `findElement` 程序。  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 上述對 `MsgBox` 的呼叫會分別顯示 "0"、"1" 和 "\-1"。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [如何：定義可以在不同資料類型上提供完全相同功能的類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [如何：使用泛型類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Parameter List](../../../../visual-basic/language-reference/statements/parameter-list.md)