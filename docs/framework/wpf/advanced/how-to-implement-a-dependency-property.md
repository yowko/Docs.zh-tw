---
title: "如何：實作相依性屬性 | Microsoft Docs"
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
  - "相依性屬性, 支援屬性"
  - "屬性, 使用相依性屬性支援"
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：實作相依性屬性
本範例示範如何使用 <xref:System.Windows.DependencyProperty> 欄位支援 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性，藉以定義[相依性屬性](GTMT)。  當您定義自己的屬性時，若想讓這些屬性支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的許多層面，包括樣式、資料繫結、繼承、動畫和預設值，您應該將它們實作成[相依性屬性](GTMT)。  
  
## 範例  
 下列範例首先會藉由呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 方法來註冊[相依性屬性](GTMT)。  用來儲存[相依性屬性](GTMT)名稱和特性的識別項欄位，必須是您在呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 時為相依性屬性選擇的 <xref:System.Windows.DependencyProperty.Name%2A>，再加上常值字串 `Property`。  例如，如果您使用 <xref:System.Windows.DependencyProperty.Name%2A> of `Location` 註冊相依性屬性，則您對相依性屬性定義的識別項欄位必須命名為 `LocationProperty`。  
  
 在這個範例中，[相依性屬性](GTMT)及其 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 存取子 \(Accessor\) 的名稱是 `State`；識別項欄位是 `StateProperty`；屬性的型別是 <xref:System.Boolean>；而註冊[相依性屬性](GTMT)的型別則是 `MyStateControl`。  
  
 如果未遵照這個命名模式，設計工具可能無法正確回報您的屬性，而且屬性系統樣式應用程式的某些方面可能無法如預期般地運作。  
  
 您也可以指定[相依性屬性](GTMT)的預設中繼資料 \(Metadata\)。  這個範例會將 `State` [相依性屬性](GTMT)的預設值註冊成 `false`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 如需實作[相依性屬性](GTMT) \(相對於只使用私用 \(Private\) 欄位支援 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性\) 之方式和原因的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
## 請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)