---
title: "ColorConvertedBitmap 標記延伸 | Microsoft Docs"
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
  - "ColorConvertedBitmap 標記延伸"
  - "XAML, ColorConvertedBitmap 標記延伸"
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# ColorConvertedBitmap 標記延伸
提供方式來指定沒有內嵌設定檔的點陣圖來源。  色彩內容\/設定檔是由 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 指定，影像來源 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 也是。  
  
## XAML Attribute Usage  
  
```  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`imageSource`|沒有設定檔之點陣圖的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|`sourceIIC`|來源設定檔組態的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。|  
|`destinationIIC`|目的設定檔組態的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
  
## 備註  
 這個標記延伸是要用來填滿一組相關的影像來源屬性值，例如 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `ColorConvertedBitmap` \(或 `ColorConvertedBitmapExtension`\) 不能用於屬性項目語法，因為值只能設定為初始建構函式上的值，也就是後面接著延伸識別項的字串。  
  
 `ColorConvertedBitmap` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記延伸都會在其屬性 \(Attribute\) 語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)