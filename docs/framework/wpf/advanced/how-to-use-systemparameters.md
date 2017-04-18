---
title: "如何：使用 SystemParameters | Microsoft Docs"
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
  - "SystemParameters 類別"
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：使用 SystemParameters
本範例說明如何存取及使用 <xref:System.Windows.SystemParameters> 的屬性，以便設定或自訂按鈕的樣式。  
  
## 範例  
 系統資源會將數個以系統為基礎的設定公開為資源，協助您建立與系統設定一致的視覺效果。  <xref:System.Windows.SystemParameters> 是一種類別，其中同時包含系統參數值屬性以及繫結至這些值的資源索引鍵。  例如，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> 是 <xref:System.Windows.SystemParameters> 屬性值，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> 則是對應的資源索引鍵。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您可以將 <xref:System.Windows.SystemParameters> 的成員當做靜態屬性使用方式來使用，或是當做動態資源參考 \(以靜態屬性值做為索引鍵\) 來使用。  如果您希望系統值在應用程式執行時自動更新，請使用動態資源參考，否則，請使用靜態參考。  資源索引鍵會將後置字元 `Key` 附加至屬性名稱。  
  
 下列範例說明如何存取及使用 <xref:System.Windows.SystemParameters> 的靜態值，以便設定或自訂按鈕的樣式。  這個標記範例會藉由將 <xref:System.Windows.SystemParameters> 值套用至按鈕，以調整按鈕大小。  
  
 [!code-xml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 若要在程式碼中使用 <xref:System.Windows.SystemParameters> 的值，您不需要使用靜態參考或動態資源參考。  請改用 <xref:System.Windows.SystemParameters> 類別的值。  雖然非索引鍵屬性是明顯定義為靜態屬性，但由系統裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行階段行為會即時重新評估屬性，並會適當地將使用者驅動的系統值變更納入考量。下列範例說明如何藉由使用 <xref:System.Windows.SystemParameters> 值來設定按鈕的寬度和高度。  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## 請參閱  
 <xref:System.Windows.SystemParameters>   
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [使用 SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [使用系統參數索引鍵](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)