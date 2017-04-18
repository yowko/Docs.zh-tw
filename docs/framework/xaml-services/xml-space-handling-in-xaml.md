---
title: "xml:space Handling in XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], xml:space attribute"
  - "XAML [XAML Services], whitespace processing"
  - "xml:space attribute [XAML Services]"
  - "whitespace processing [XAML Services]"
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:space Handling in XAML
`xml:space` 屬性是 XML 定義的屬性，會宣告物件項目內的顯著空白字元處理行為。  這項行為與項目內包含的所有內容 \(內部文字\) 相關，其中宣告 `xml:space`，而且範圍也包括子項目。  
  
## XAML Attribute Usage  
  
```  
<object xml:space="preserve" />  
```  
  
 \-或\-  
  
```  
<object xml:space="default" />  
```  
  
## 備註  
 XAML 中 `xml:space` 屬性的定義 \(包括兩個可能的值\)，都是從由 XML 的 W3C 規格定義為「特殊屬性」的 `xml:space` 所衍生。  
  
 `xml:space` 屬性的預設值是常值 `"default"`。  若為值 `"default"`，或完全未指定 `xml:space`，則如同 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)主題所定義，必要空白字元剖析的行為即是預設處理。  
  
 若要將空白字元保留在物件項目內容中，請指定在該物件項目上指定 `xml:space="preserve"`。  
  
 在多數解譯之下，`xml:space` 屬性效果和屬性值的範圍都會擴及至子項目。  
  
 如需 XAML 中空白字元處理的完整討論，請參閱 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
## 請參閱  
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)   
 [XAML 概觀 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)