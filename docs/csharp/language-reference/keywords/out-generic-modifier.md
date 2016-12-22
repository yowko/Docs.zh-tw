---
title: "out (泛型修飾詞) (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "共變數, out 關鍵字 [C#]"
  - "out 關鍵字 [C#]"
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# out (泛型修飾詞) (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

就泛型型別參數而言，`out` 關鍵字會指定型別參數為 Covariant。  您可以在泛型介面及委派中使用 `out` 關鍵字。  
  
 共變數允許您使用與泛型參數指定的型別相比，其衍生程度較大的型別。  這樣可以允許實作 Variant 介面的類別進行隱含轉換，以及委派型別的隱含轉換。  參考型別會支援共變數和 Contravariance，但是實值型別則不支援。  
  
 具有 Covariant 型別參數的介面允許其方法傳回與介面型別參數指定的型別相比，其衍生程度較大的型別。  例如，在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，由於型別 T 為 Covariant，因此可以將型別為 `IEnumerabe(Of String)` 的物件指派給型別為 `IEnumerable(Of Object)` 的物件，而不需使用任何特別的轉換方法。  
  
 您可以將其他相同型別的委派指派給 Covariant 委派，但是前者要有衍生程度較大的泛型型別參數。  
  
 如需詳細資訊，請參閱 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列範例示範如何宣告、擴充和實作 Covariant 泛型介面，  同時也示範如何對實作 Covariant 介面的類別使用隱含轉換。  
  
 [!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 在泛型介面中，如果型別參數滿足下列條件，您就可以將它宣告為 Covariant：  
  
-   型別參數只當做介面方法的傳回型別，而不能當做方法引數的型別使用。  
  
    > [!NOTE]
    >  這個規則只有一個例外。  如果 Covariant 介面中有當做方法參數的 Contravariant 泛型委派，則可以使用 Covariant 型別做為這個委派的泛型型別參數。  如需 Covariant 及 Contravariant 泛型委派的詳細資訊，請參閱[委派中的變異數](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)和[針對 Func 與 Action 委派使用變異數](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)。  
  
-   型別參數不能當做介面方法的泛型條件約束使用。  
  
## 範例  
 下列範例示範如何宣告、執行個體化和叫用 Covariant 泛型委派，  同時也示範如何隱含轉換委派型別。  
  
 [!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 在泛型委派中，如果型別只當做方法傳回型別，而不當做方法引數使用，就可以將它宣告為 Covariant。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [泛型介面中的變異數](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)