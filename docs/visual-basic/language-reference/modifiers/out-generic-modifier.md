---
title: "Out (Generic Modifier) (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.VarianceOut"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Out keyword [Visual Basic]"
  - "covariance, Out keyword [Visual Basic]"
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Out (Generic Modifier) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

就泛型型別參數而言，`Out` 關鍵字會指定型別為 Covariant。  
  
## 備註  
 共變數允許您使用與泛型參數指定的型別相比，其衍生程度較大的型別。  這樣可以允許實作 Variant 介面的類別進行隱含轉換，以及委派型別的隱含轉換。  
  
 如需詳細資訊，請參閱 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 規則  
 您可以在泛型介面及委派中使用 `Out` 關鍵字。  
  
 在泛型介面中，如果型別參數滿足下列條件，您就可以將它宣告為 Covariant：  
  
-   型別參數只當做介面方法的傳回型別，而不能當做方法引數的型別使用。  
  
    > [!NOTE]
    >  這個規則只有一個例外。  如果 Covariant 介面中有當做方法參數的 Contravariant 泛型委派，則可以使用 Covariant 型別做為這個委派的泛型型別參數。  如需 Covariant 及 Contravariant 泛型委派的詳細資訊，請參閱[委派中的變異數](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)和[針對 Func 與 Action 委派使用變異數](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)。  
  
-   型別參數不能當做介面方法的泛型條件約束使用。  
  
 在泛型委派中，如果型別參數只當做方法傳回型別，而不當做方法引數使用，就可以將它宣告為 Covariant。  
  
 參考型別會支援共變數和 Contravariance，但是實值型別則不支援。  
  
 在 Visual Basic 中，您無法在不指定委派型別的情況下，宣告 Covariant 介面中的事件。  此外，Covariant 介面也不能有巢狀類別、列舉或結構，但是可以有巢狀介面。  
  
## 行為  
 具有 Covariant 型別參數的介面允許其方法傳回與介面型別參數指定的型別相比，其衍生程度較大的型別。  例如，在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，由於型別 T 為 Covariant，因此可以將型別為 `IEnumerabe(Of String)` 的物件指派給型別為 `IEnumerable(Of Object)` 的物件，而不需使用任何特別的轉換方法。  
  
 您可以將其他相同型別的委派指派給 Covariant 委派，但是前者要有衍生程度較大的泛型型別參數。  
  
## 範例  
 下列範例示範如何宣告、擴充和實作 Covariant 泛型介面，  同時也示範如何對實作 Covariant 介面的類別使用隱含轉換。  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/out-generic-modifier_1.vb)]  
  
## 範例  
 下列範例示範如何宣告、執行個體化和叫用 Covariant 泛型委派，  同時也示範如何對委派型別使用隱含轉換。  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/out-generic-modifier_2.vb)]  
  
## 請參閱  
 [泛型介面中的變異數](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)