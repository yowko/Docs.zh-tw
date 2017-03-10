---
title: "sealed (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sealed"
  - "sealed_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sealed 關鍵字 [C#]"
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# sealed (C# 參考)
套用至類別時，`sealed` 修飾詞會防止其他類別繼承該類別。  在下列範例中，`B` 繼承自類別 `A`，但沒有任何類別可繼承自 `B`。  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 您也可以在方法或屬性上使用 `sealed` 修飾詞，而該方法或屬性會覆寫基底類別中的虛擬方法或屬性。  這可讓您允許從您的類別衍生類別，並防止這些類別覆寫特定的虛擬方法或屬性。  
  
## 範例  
 在下列範例中，`Z` 繼承自 `Y`，但 `Z` 無法覆寫已在 `X` 中宣告，並在 `Y` 中密封的虛擬函式 `F`。  
  
 [!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#16)]  
  
 當您在類別中定義新方法或屬性時，可以不將這些方法或屬性宣告為 [virtual](../../../csharp/language-reference/keywords/virtual.md)，以防止衍生類別被它們所覆寫。  
  
 搭配使用 [abstract](../../../csharp/language-reference/keywords/abstract.md) 修飾詞與密封類別會導致錯誤，因為抽象類別必須是由提供抽象方法或屬性之實作的類別所繼承。  
  
 當套用至方法或屬性時，`sealed` 修飾詞必須一律和 [override](../../../csharp/language-reference/keywords/override.md) 搭配使用。  
  
 因為結構 \(Struct\) 是隱含密封的，所以無法繼承。  
  
 如需詳細資訊，請參閱 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
 如需更多範例，請參閱 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## 範例  
 [!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#17)]  
  
 在前一個範例中，您會使用下列陳述式從密封類別繼承：  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 會產生錯誤訊息：  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 備註  
 若要判斷是否要密封類別、方法或屬性，您應該考量下列兩點：  
  
-   衍生類別可透過自訂類別的能力所得到的潛在優點。  
  
-   衍生類別可修改類別的可能性，不過使用的方法可能無法正常或如預期運作。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [虛擬](../../../csharp/language-reference/keywords/virtual.md)