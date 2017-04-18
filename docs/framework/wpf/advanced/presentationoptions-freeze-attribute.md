---
title: "PresentationOptions:Freeze 屬性 | Microsoft Docs"
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
  - "可凍結的項目"
  - "Freeze 屬性"
  - "PresentationOptions 前置詞"
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# PresentationOptions:Freeze 屬性
在包含的 <xref:System.Windows.Freezable> 項目上，將 <xref:System.Windows.Freezable.IsFrozen%2A> 狀態設定為 `true`。  未指定 `PresentationOptions:Freeze` 屬性 \(Attribute\) 之 <xref:System.Windows.Freezable> 的預設行為如下：<xref:System.Windows.Freezable.IsFrozen%2A> 在載入時間 \(Load Time\) 為 `false`，而在執行階段則取決於一般的 <xref:System.Windows.Freezable> 行為。  
  
## XAML Attribute Usage  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`PresentationOptions`|XML 命名空間前置字元；依據 XML 1.0 規格，此項目可以做為任何有效的前置字串。  在本文件中，前置字元 `PresentationOptions` 可用於識別目的。|  
|`freezableElement`|用來執行個體化 <xref:System.Windows.Freezable> 之任何衍生類別 \(Derived Class\) 的項目。|  
  
## 備註  
 `Freeze` 屬性是 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 命名空間中定義的唯一屬性或其他程式設計項目。  `Freeze` 屬性特別存在於此特殊命名空間，因此可以使用 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)做為根項目 \(Root Element\) 宣告的一部分，將它指定為可忽略。  `Freeze` 必須為可忽略的原因在於，並非所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器實作都能夠在載入時間凍結 <xref:System.Windows.Freezable>；這項功能不屬於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 規格。  
  
 處理 `Freeze` 屬性的功能，已特別建置在負責處理已編譯應用程式之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器中。  此屬性不受任何類別支援，而且屬性語法無法擴充也無法修改。  如果您實作自己的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器，可以選擇在載入時間處理 <xref:System.Windows.Freezable> 項目上的 `Freeze` 屬性時，同時採用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的凍結行為。  
  
 除了 `true` \(不區分大小寫\) 以外，`Freeze` 屬性的任何值都會產生載入時間錯誤   \(將 `Freeze` 屬性指定為 `false` 不是錯誤，但這個值已經是預設值，所以設定為 `false` 不會有任何作用\)。  
  
## 請參閱  
 <xref:System.Windows.Freezable>   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)