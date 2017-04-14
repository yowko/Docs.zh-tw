---
title: "如何：使用 SystemFonts | Microsoft Docs"
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
  - "字型, 系統字型"
  - "系統字型"
  - "SystemFonts 類別"
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 如何：使用 SystemFonts
本範例說明如何使用 <xref:System.Windows.SystemFonts> 類別的靜態資源，以便設定或自訂按鈕的樣式。  
  
## 範例  
 系統資源會將數個系統判斷的值同時公開為資源和屬性，協助您建立與系統設定一致的視覺效果。  <xref:System.Windows.SystemFonts> 是一種類別，其中同時包含做為靜態屬性的系統字型值，以及參考可在執行階段動態存取這些值之資源索引鍵的屬性。  例如，<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> 是 <xref:System.Windows.SystemFonts> 值，<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> 則是對應的資源索引鍵。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您可以將 <xref:System.Windows.SystemFonts> 的成員當做靜態屬性來使用，或是當做動態資源參考 \(以靜態屬性值做為索引鍵\) 來使用。  如果您希望字型度量資訊在應用程式執行時自動更新，請使用動態資源參考，否則，請使用靜態值參考。  
  
> [!NOTE]
>  資源索引鍵會將後置字元 "Key" 附加至屬性名稱。  
  
 下列範例說明如何存取及使用 <xref:System.Windows.SystemFonts> 的屬性做為靜態值，以便設定或自訂按鈕的樣式。  這個標記範例會將 <xref:System.Windows.SystemFonts> 值指派給按鈕。  
  
 [!code-xml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 若要在程式碼中使用 <xref:System.Windows.SystemFonts> 的值，您不需要使用靜態值或動態資源參考。  請改用 <xref:System.Windows.SystemFonts> 類別的非索引鍵屬性。  雖然非索引鍵屬性是明顯定義為靜態屬性，但由系統裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行階段行為會即時重新評估屬性，並會適當地將使用者對於系統值所做的變更納入考量。  下列範例顯示如何指定按鈕的字型設定。  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## 請參閱  
 <xref:System.Windows.SystemFonts>   
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [使用 SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [使用系統字型索引鍵](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)   
 [x:Static 標記延伸](../../../../docs/framework/xaml-services/x-static-markup-extension.md)   
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)