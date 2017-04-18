---
title: "初始化物件樹狀結構以外的物件項目 | Microsoft Docs"
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
  - "項目, 初始化"
  - "初始化項目"
  - "邏輯樹狀結構"
  - "視覺化樹狀結構"
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 初始化物件樹狀結構以外的物件項目
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 初始設定的某些部分已延後到某些處理序，而這些處理序通常依賴連接至[邏輯樹狀結構](GTMT)或[視覺化樹狀結構](GTMT)的項目。  本主題說明為了初始化未連接到這兩個樹狀目錄的項目，您可能需要採取的步驟。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 項目和邏輯樹狀結構  
 在程式碼中建立 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的執行個體時，您應該了解，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的物件初始設定有幾個層面並不屬於呼叫類別建構函式時所執行之程式碼的一部分。  特別是控制項類別，該控制項的視覺化呈現大都不是由建構函式定義，  而是由控制項的樣板定義。  樣板可能來自各種不同的來源，但通常是從主題佈景樣式取得。  樣板實際上是晚期繫結 \(Late\-Binding\)；必須等到相關控制項可以開始配置時，必要的樣板才會附加到該控制項，  而控制項則必須等到附加至邏輯樹狀結構 \(連接到根目錄的呈現介面\) 之後才可以開始配置。  其於邏輯樹狀結構中定義的所有子項目都是由該根層級項目加以啟始。  
  
 視覺化樹狀結構也會參與此程序。  透過樣板成為視覺樹狀結構一部分的項目，也必須等到連接之後才會完全具現化 \(Instantiated\)。  
  
 這個行為的結果是依賴項目完整視覺特性的某些作業需要執行額外的步驟。  例如，如果您嘗試取得某個類別的視覺化特性，但是該類別雖已建構完成卻尚未附加至樹狀結構。  舉例來說，如果您想在 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 上呼叫 <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A>，而您所傳遞的視覺效果是尚未連接至樹狀結構的項目，則必須等到完成額外的初始設定步驟之後，該項目才會呈現完整的視覺效果。  
  
### 使用 BeginInit 和 EndInit 來初始化項目  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的各種類別均可實作 <xref:System.ComponentModel.ISupportInitialize> 介面。  您可使用此介面的 <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> 和 <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> 方法來代表程式碼中包含初始設定步驟 \(例如設定影響呈現效果的屬性值\) 的區域。  在呼叫序列中的 <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> 之後，配置系統可以處理項目並開始尋找隱含樣式。  
  
 如果您要設定屬性的項目是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生類別 \(Derived Class\)，則您可以呼叫 <xref:System.Windows.FrameworkElement.BeginInit%2A> 和 <xref:System.Windows.FrameworkElement.EndInit%2A> 的版本，而非轉換成 <xref:System.ComponentModel.ISupportInitialize>。  
  
### 程式碼範例  
 下列範例是主控台應用程式的範例程式碼，它使用鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的呈現 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 和 <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=fullName>，說明如何將 <xref:System.Windows.FrameworkElement.BeginInit%2A> 和 <xref:System.Windows.FrameworkElement.EndInit%2A> 正確放置在可調整影響呈現之屬性的其他 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼叫前後。  
  
 此範例僅顯示主要的函式。  `Rasterize` 和 `Save` 函式 \(未顯示\) 是負責影像處理和 IO 的公用程式函式。  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## 請參閱  
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)