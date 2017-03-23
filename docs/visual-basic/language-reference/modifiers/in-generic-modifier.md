---
title: "In (Generic Modifier) (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.VarianceIn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "contravariance, In keyword [Visual Basic]"
  - "In keyword [Visual Basic]"
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# In (Generic Modifier) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

就泛型型別參數而言，`In` 關鍵字會指定型別參數為 Contravariant。  
  
## 備註  
 Contravariance 允許您使用與泛型參數指定的型別相比，其衍生程度較小的型別。  這樣可以允許實作 Variant 介面的類別進行隱含轉換，以及委派型別的隱含轉換。  
  
 如需詳細資訊，請參閱 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 規則  
 您可以在泛型介面及委派中使用 `In` 關鍵字。  
  
 如果使用型別參數做為方法引數的型別，而非做為方法傳回型別，即可在泛型介面或委派中將其宣告為 Contravariant。  `ByRef` 參數不能是 Covariant 或 Contravariant。  
  
 參考型別會支援共變數和 Contravariance，但是實值型別則不支援。  
  
 在 Visual Basic 中，您無法在不指定委派型別的情況下，宣告 Contravariant 介面中的事件。  此外，Contravariant 介面也不能有巢狀類別、列舉或結構，但是可以有巢狀介面。  
  
## 行為  
 具有 Contravariant 型別參數的介面允許其方法接受與介面型別參數指定的型別相比，其衍生程度較小之型別的引數。  例如，在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，由於型別 T 為 Contravariant，因此只要 `Person` 會繼承 `Employee`，就可以將型別為 `IComparer(Of Person)` 的物件指派給型別為 `IComparer(Of Employee)` 的物件，而不需使用任何特別的轉換方法。  
  
 您可以將其他相同型別的委派指派給 Contravariant 委派，但是前者要有衍生程度較小的泛型型別參數。  
  
## 範例  
 下列範例示範如何宣告、擴充和實作 Contravariant 泛型介面，  同時也示範如何在實作此介面的類別中使用隱含轉換。  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## 範例  
 下列範例示範如何宣告、執行個體化和叫用 Contravariant 泛型委派，  同時也示範如何才能隱含轉換委派型別。  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## 請參閱  
 [泛型介面中的變異數](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)