---
title: "文件序列化與儲存 | Microsoft Docs"
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
  - "文件, 序列化"
  - "文件, 儲存體"
  - "文件序列化"
  - "文件的儲存"
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 文件序列化與儲存
[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 提供強大的環境來建立和顯示高品質的文件。  增強的功能包括同時支援固定文件和非固定格式文件、進階檢視控制項，再加上強大的 2D 和 3D 圖形功能，可將 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式帶往更高品質和使用者經驗的全新境界。  彈性管理記憶體中的文件呈現，是 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 的一項重要功能，而有效儲存和載入資料存放區中的文件則幾乎是每一項應用程式都需要的功能。  將文件從內部記憶體中呈現轉換至外部資料儲存區的程序，稱為[序列化](GTMT) \(Serialization\)。  反之，讀取資料存放區再重新建立原始記憶體中執行個體的程序，則稱為還原序列化 \(Deserialization\)。  
  
   
  
<a name="AboutSerialization"></a>   
## 關於文件序列化  
 在理想狀況下，與記憶體之間進行的文件[序列化](GTMT)和還原序列化程序對於應用程式而言應該是透明的。  應用程式會呼叫序列化程式的 "write" 方法來儲存文件，而還原序列化程式的 "read" 方法則會存取資料存放區並在記憶體中重新建立原始執行個體。  只要序列化和還原序列化程序會將文件重新建立成原始格式，資料是以哪種格式儲存對應用程式而言通常並不重要。  
  
 應用程式通常會提供多種序列化選項，供使用者將文件儲存到不同媒體或不同格式。  例如，應用程式可能會提供 \[另存新檔\] 選項以將文件儲存至磁碟檔案、資料庫或 Web 服務。  同樣地，不同的序列化程式可能會將文件儲存成不同格式，例如 HTML、RTF、XML、XPS 或其他協力廠商格式。  對應用程式而言，序列化定義了一個介面，可將每個特定序列化程式實作時的儲存媒體詳細資訊加以隔離。  除了可將儲存詳細資料封裝起來的好處之外，[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 另外還提供數項重要功能。  
  
### .NET Framework 3.0 文件序列化程式的功能  
  
-   直接存取高階文件物件 \([邏輯樹狀結構](GTMT)和視覺物件\) 可以有效儲存已編頁的內容、2D\/3D 項目、影像、媒體、超連結、附註和其他支援內容。  
  
-   [同步](GTMT)和[非同步](GTMT)作業 \(Asynchronous Operation\)。  
  
-   使用增強的功能支援外掛程式序列化程式：  
  
    -   供所有 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式使用的系統範圍存取權  
  
    -   輕鬆探索應用程式外掛程式  
  
    -   輕鬆部署、安裝和更新自訂的協力廠商外掛程式  
  
    -   可支援自訂執行階段設定和選項的使用者介面  
  
### XPS 列印路徑  
 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 列印路徑也提供可擴充機制，透過列印輸出的方式寫入文件。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 可同時做為文件檔案格式，以及 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 的原生列印多工緩衝區格式。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文件可以直接傳送至 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 相容的印表機，而不需要轉換成中繼格式。  如需列印路徑輸出選項和功能的詳細資訊，請參閱[列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)。  
  
<a name="PluginSerializers"></a>   
## 外掛程式序列化程式  
 <xref:System.Windows.Documents.Serialization> API 可同時支援外掛程式序列化程式和連結的序列化程式，這些序列化程式的特點是它們是與應用程式分開安裝的、在執行階段才繫結，而且是透過 <xref:System.Windows.Documents.Serialization.SerializerProvider> 探索 \(Discovery\) 機制來存取。  外掛程式序列化程式可提供增強的優點，例如易於部署和整個系統範圍的使用。  在禁止存取外掛程式序列化程式的[部分信任](GTMT)環境中 \(例如 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]\)，也可以實作連結的序列化程式。  連結的序列化程式 \(根據 <xref:System.Windows.Documents.Serialization.SerializerWriter> 類別的衍生實作而來\) 會先編譯再直接連結至應用程式中。  外掛程式序列化程式和連結的序列化程式都是透過相同的公用方法和事件運作，因此您可以很輕易地在同一個應用程式中使用其中一種 \(或兩種都使用\) 序列化程式。  
  
 外掛程式序列化程式可以協助應用程式開發人員擴充新的儲存設計和檔案格式，而不需要針對建置階段可能出現的每種格式直接撰寫程式碼。  外掛程式序列化程式同時也能夠提供協力廠商開發人員標準化的方法，來針對自訂或專屬檔案格式部署、安裝和更新可供系統存取的外掛程式。  
  
### 使用外掛程式序列化程式  
 外掛程式序列化程式的使用方法很簡單。  <xref:System.Windows.Documents.Serialization.SerializerProvider> 類別會針對系統上安裝的每個外掛程式各列舉一個 <xref:System.Windows.Documents.Serialization.SerializerDescriptor> 物件。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> 屬性會根據目前的組態篩選已安裝的外掛程式，然後確認應用程式可以載入和使用該序列化程式。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> 同時也提供 <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> 和 <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A> 等其他屬性，應用程式會使用這些屬性來提示使用者選取可用之輸出格式的序列化程式。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 的預設外掛程式序列化程式會隨 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 提供，而且一律會被列舉。  在使用者選取輸出格式之後，即會使用 <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> 方法來建立特定格式適用的 <xref:System.Windows.Documents.Serialization.SerializerWriter>。  接著可呼叫 <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> 方法將文件資料流輸出至資料存放區。  
  
 下列範例會說明如何在應用程式的 "PlugInFileFilter" 屬性中使用 <xref:System.Windows.Documents.Serialization.SerializerProvider> 方法。  PlugInFileFilter 會列舉已安裝的外掛程式，然後使用 <xref:Microsoft.Win32.SaveFileDialog> 的可用檔案選項來建置篩選條件字串。  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 在使用者選取輸出檔案名稱之後，下列範例會說明如何使用 <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> 方法來以指定的格式儲存特定文件。  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### 安裝外掛程式序列化程式  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> 類別會針對外掛程式序列化程式的探索和存取作業提供高階應用程式介面。  <xref:System.Windows.Documents.Serialization.SerializerProvider> 會尋找系統上已安裝且可存取的序列化程式，並且列成清單提供給應用程式。  已安裝之序列化程式的內容是透過登錄設定定義。  外掛程式序列化程式可以透過 <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> 方法加入至登錄中。如果尚未安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，則外掛程式安裝指令碼可以親自設定登錄值。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> 方法可用於移除先前安裝的外掛程式。同樣地，藉由解除安裝指令碼可以重新設定登錄設定。  
  
### 建立外掛程式序列化程式  
 外掛程式序列化程式和連結的序列化程式都是使用同樣一組公開的公用方法和事件，而且都可以設計成[同步](GTMT)或[非同步](GTMT)運作。  若要建立外掛程式序列化程式，通常要遵循三個基本步驟：  
  
1.  首先將序列化程式實作為連結的序列化程式並加以偵錯。  一開始就建立已編譯的序列化程式並將之直接連結到測試應用程式中，將可以完整存取中斷點和其他有助於進行測試的偵錯服務。  
  
2.  在完整測試過序列化程式之後，加入 <xref:System.Windows.Documents.Serialization.ISerializerFactory> 介面來建立外掛程式。  <xref:System.Windows.Documents.Serialization.ISerializerFactory> 介面允許完整存取所有 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 物件，包括邏輯樹狀結構、<xref:System.Windows.UIElement> 物件、<xref:System.Windows.Documents.IDocumentPaginatorSource> 和 <xref:System.Windows.Media.Visual> 項目。  此外，<xref:System.Windows.Documents.Serialization.ISerializerFactory> 也提供連結的序列化程式會使用的相同同步和非同步方法。  由於大型文件的輸出作業較費時，因此建議採用非同步作業以與使用者維持良好互動，並同時提供 \[取消\] 選項以防萬一資料存放區發生問題。  
  
3.  在建立外掛程式序列化程式之後，實作散發和安裝 \(以及解除安裝\) 外掛程式用的安裝指令碼 \(請參閱上述的[安裝外掛程式序列化程式](#InstallingPluginSerializers)\)。  
  
## 請參閱  
 <xref:System.Windows.Documents.Serialization>   
 <xref:System.Windows.Xps.XpsDocumentWriter>   
 <xref:System.Windows.Xps.Packaging.XpsDocument>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [XML 文件規格：概觀](http://go.microsoft.com/fwlink/?LinkID=106246)