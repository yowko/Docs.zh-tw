---
title: "Property let procedure not defined and property get procedure did not return an object | Microsoft Docs"
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
  - "vbrID451"
dev_langs: 
  - "VB"
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property let procedure not defined and property get procedure did not return an object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

部分屬性、方法和作業只能套用至 `Collection` 物件。  您指定的作業或屬性對集合是獨佔的，但該物件不是集合。  
  
### 若要更正這個錯誤  
  
1.  請檢查物件或屬性名稱的拼字，或者驗證物件是否為 `Collection` 物件。  
  
2.  請檢視用來將物件加入至集合的 `Add` 方法，以確定語法的正確性，以及所有識別項的拼字是否正確。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Collection>