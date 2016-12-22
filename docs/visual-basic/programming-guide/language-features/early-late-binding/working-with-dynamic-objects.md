---
title: "Working with Dynamic Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dynamic objects [Visual Basic]"
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Working with Dynamic Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

動態物件提供除了 `Object` 型別以外，在執行階段晚期繫結至物件的另一種方法。  動態物件會使用 <xref:System.Dynamic> 命名空間中定義的動態介面，在執行階段公開屬性和方法等成員。  您可以使用 <xref:System.Dynamic> 命名空間中的類別來建立物件，以處理不符合靜態類型或格式的資料結構，  也可以使用以 IronPython 和 IronRuby 等動態語言定義的動態物件。  如需如何建立動態物件或使用動態語言中定義之動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、<xref:System.Dynamic.DynamicObject> 或 <xref:System.Dynamic.ExpandoObject>。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 使用 <xref:System.Dynamic.IDynamicMetaObjectProvider> 介面，從 Dynamic Language Runtime 以及 IronPython 和 IronRuby 之類的動態語言繫結至物件。  實作 `IDynamicMetaObjectProvider` 介面的類別範例為 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。  
  
 如果對實作 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 就會使用該介面繫結至動態物件。  如果對未實作 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，或是呼叫 `IDynamicMetaObjectProvider` 介面失敗，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會使用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 執行階段的晚期繫結功能繫結至該物件。  
  
## 請參閱  
 <xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject>   
 [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)