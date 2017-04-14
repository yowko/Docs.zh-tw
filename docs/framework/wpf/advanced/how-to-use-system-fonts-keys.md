---
title: "如何：使用系統字型索引鍵 | Microsoft Docs"
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
  - "類別, SystemFonts"
  - "資源索引鍵, SystemFonts 類別"
  - "SystemFonts 類別"
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用系統字型索引鍵
系統資源會將數個系統度量資訊 \(Metric\) 公開為資源，協助開發人員建立與系統設定一致的視覺效果。  <xref:System.Windows.SystemFonts> 是一種類別，同時包含系統字型值以及繫結至這些值的系統字型資源 \(例如，<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> 和 <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>\)。  
  
 系統字型度量資訊可以當成靜態或動態資源使用。  如果想要在應用程式執行時自動更新字型度量資訊，請使用動態資源，否則請使用靜態資源。  
  
> [!NOTE]
>  動態資源會在屬性名稱後面加上關鍵字 *Key*。  
  
 下列範例顯示如何存取和使用系統字型動態資源，以設定或自訂按鈕的樣式。  這個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例會建立將 <xref:System.Windows.SystemFonts> 值指派給按鈕的按鈕樣式。  
  
## 範例  
 [!code-xml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## 請參閱  
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [使用 SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [使用 SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)