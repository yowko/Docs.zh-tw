---
title: "First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30148"
  - "vbc30148"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30148"
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New'，因為 '\<derivedname\>' 的基底類別 \(Base Class\)'\<basename\>' 沒有不用引數即可呼叫存取的 'Sub New'。  
  
 在衍生類別中，每一個建構函式都必須呼叫基底類別建構函式 \(`MyBase.New`\)。  如果基底類別的建構函式沒有參數，而衍生類別可以存取該建構函式，就會自動呼叫 `MyBase.New`。  如果沒有，則必須用參數呼叫基底類別建構函式，且無法自動呼叫。  在本狀況中，每個衍生類別建構函式的第一個陳述式，必須呼叫基底類別上的參數型建構函式，或呼叫建立基底類別建構函式呼叫之衍生類別中的另一個建構函式。  
  
 **錯誤 ID**︰BC30148  
  
### 若要更正這個錯誤  
  
-   請呼叫 `MyBase.New` 並提供所需的參數，或是呼叫建立這類呼叫的對等建構函式。  
  
     例如，如果基底類別的建構函式宣告為`Public Sub New(ByVal index as Integer)`、 第一個陳述式，在衍生類別建構函式可能是`MyBase.New(100)`。  
  
## 請參閱  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)