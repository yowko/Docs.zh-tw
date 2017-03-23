---
title: "in (泛型修飾詞) (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "反變數, in 關鍵字 [C#]"
  - "in 關鍵字 [C#]"
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# in (泛型修飾詞) (C# 參考)
就泛型型別參數而言，`in` 關鍵字會指定型別參數為 Contravariant。  您可以在泛型介面及委派中使用 `in` 關鍵字。  
  
 Contravariance 允許您使用與泛型參數指定的型別相比，其衍生程度較小的型別。  這樣可以允許實作 Variant 介面的類別進行隱含轉換，以及委派型別的隱含轉換。  參考型別會支援泛型型別參數中的共變數和 Contravariance，但是實值型別則不支援。  
  
 如果使用型別做為方法引數的型別，而非做為方法傳回型別，即可在泛型介面或委派中將其宣告為 Contravariant。  `Ref` 和 `out` 參數不可為變數。  
  
 具有 Contravariant 型別參數的介面允許其方法接受與介面型別參數指定的型別相比，其衍生程度較小之型別的引數。  例如，在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，由於型別 T 為 Contravariant，因此只要 `Employee` 會繼承 `Person`，就可以將型別為 `IComparer(Of Person)` 的物件指派給型別為 `IComparer(Of Employee)` 的物件，而不需使用任何特別的轉換方法。  
  
 您可以將其他相同型別的委派指派給 Contravariant 委派，但是前者要有衍生程度較小的泛型型別參數。  
  
 如需詳細資訊，請參閱 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列範例示範如何宣告、擴充和實作 Contravariant 泛型介面，  同時也示範如何在實作此介面的類別中使用隱含轉換。  
  
 [!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## 範例  
 下列範例示範如何宣告、執行個體化和叫用 Contravariant 泛型委派，  同時也示範如何才能隱含轉換委派型別。  
  
 [!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)   
 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)