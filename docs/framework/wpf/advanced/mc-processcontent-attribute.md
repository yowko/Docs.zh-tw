---
title: "mc:ProcessContent 屬性 | Microsoft Docs"
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
  - "mc:ProcessContent 屬性"
  - "XAML, mc:ProcessContent 屬性"
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# mc:ProcessContent 屬性
指定哪些 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目應仍有由相關父項目處理的內容，即使直接父項目因為指定了 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) 而為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器所忽略。  `mc:ProcessContent` 屬性 \(Attribute\) 可支援同時適用於自訂命名空間對應和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 版本控制的標記相容性。  
  
## XAML Attribute Usage  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*ignorablePrefix*|依據 XML 1.0 規格，任何有效的前置字串。|  
|*ignorableUri*|依據 XML 1.0 規格，用來指定命名空間的任何有效 URI。|  
|*ThisElementCanBeIgnored*|無法解析基礎型別時，[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 處理器實作可以忽略的項目。|  
|*\[content\]*|*ThisElementCanBeIgnored* 標記為可忽略的。  如果處理器忽略該項目，*\[content\]* 就會由 *object* 處理。|  
  
## 備註  
 根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器會忽略已忽略之項目的內容。  您可以指定特定項目為 `mc:ProcessContent`，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器就會繼續處理已忽略之項目的內容。  一般如果內容以巢狀方式置於數個標記內，而其中至少有一個是可忽略，且其中至少有一個是不可忽略的，就會使用上述方式。  
  
 您可以在屬性中指定多個前置詞，並使用空白分隔符號隔開，例如：`mc:ProcessContent="ignore:Element1 ignore:Element2"`。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] 命名空間會定義[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 的這個區域內未記載的其他項目和屬性。  如需詳細資訊，請參閱 [XML 標記相容性規格](http://go.microsoft.com/fwlink/?LinkId=73824) \(英文\)。  
  
## 請參閱  
 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)