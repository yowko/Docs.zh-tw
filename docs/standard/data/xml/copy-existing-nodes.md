---
title: "複製現有節點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 複製現有節點
XML 文件物件模型 \(DOM\) 中有許多方法和屬性可讓您用來選取節點，如 **SelectSingleNode**、**ChildNodes\[int i\]**、**Attributes\[int i\]** 等。  一旦選取節點之後，您可以使用處理特殊節點型別的其中一種插入方法，將它插入至樹狀結構。  將節點插入樹狀結構的唯一限制是，文件在節點插入後仍必須保持正確格式。  現有節點插入 DOM 樹狀結構時，即會從它的原始位置移除，然後加入其目標位置中。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)