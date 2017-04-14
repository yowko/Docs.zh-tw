---
title: "如何：使用系統參數索引鍵 | Microsoft Docs"
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
  - "類別, SystemParameters"
  - "資源索引鍵, SystemParameters 類別"
  - "SystemParameters 類別"
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：使用系統參數索引鍵
系統資源會將數個系統度量資訊 \(Metric\) 公開為資源，協助開發人員建立與系統設定一致的視覺效果。  <xref:System.Windows.SystemParameters> 是一種類別，同時包含系統參數值以及繫結至這些值的資源索引鍵 \(例如，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> 和 <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>\)。  系統參數度量資訊可以當成靜態或動態資源使用。  如果想要在應用程式執行時自動更新參數度量資訊，請使用動態資源，否則請使用靜態資源。  
  
> [!NOTE]
>  動態資源會在屬性名稱後面加上關鍵字 *Key*。  
  
 下列範例顯示如何存取和使用系統參數動態資源，以設定或自訂按鈕的樣式。  這個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例會為按鈕的寬度與高度指派 <xref:System.Windows.SystemParameters> 值，以設定按鈕的大小。  
  
## 範例  
 [!code-xml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## 請參閱  
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [使用 SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [使用 SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)