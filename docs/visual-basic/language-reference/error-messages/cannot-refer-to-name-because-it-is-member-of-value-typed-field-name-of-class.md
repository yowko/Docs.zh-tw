---
title: "Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class | Microsoft Docs"
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
  - "vbc30310"
  - "bc30310"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30310"
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`System.MarshalByRefObject` 類別可以讓支援遠端物件存取的應用程式跨應用程式定義域界限存取物件。  跨應用程式定義域界限使用型別時，型別必須繼承自 `MarshalByRejectObject`。  無法在建立物件成員的應用程式定義域外使用物件成員，因此不可複製物件的狀態。  
  
 **錯誤 ID︰**BC30310  
  
### 若要更正這個錯誤  
  
1.  檢查參考以確定被參考的成員是有效的。  
  
2.  利用 `Me` 關鍵字明確地限定成員。  
  
## 請參閱  
 <xref:System.MarshalByRefObject>   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)