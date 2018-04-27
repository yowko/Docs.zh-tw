---
title: 文件序列化與儲存
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e65a20323e3797d6d56ac7941e4ac9aeeb0ed473
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="document-serialization-and-storage"></a>文件序列化與儲存
Microsoft.NET Framework 提供一種強大的環境建立及顯示高品質的文件。  增強的功能包括同時支援固定文件和非固定格式文件、進階檢視控制項，再加上強大的 2D 和 3D 圖形功能，可將 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式帶往更高品質和使用者體驗的全新境界。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 的一項重要功能，就是能夠彈性地管理在記憶體內部表示的文件，而幾乎所有應用程式都必須能夠有效率地將文件儲存至資料存放區，以及從資料存放區載入文件。  將文件從記憶體內部表示轉換成外部資料存放區的程序，稱為序列化。  讀取資料存放區並重新建立原始記憶體內部執行個體的反向程序，則稱為還原序列化。  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>關於文件序列化  
 在理想情況下，與記憶體之間進行的文件序列化和還原序列化程序，對於應用程式而言是透明的。  應用程式會呼叫序列化程式的 "write" 方法來儲存文件，而還原序列化程式的 "read" 方法則會存取資料存放區並在記憶體中重新建立原始執行個體。  只要序列化和還原序列化程序會將文件重新建立成原始格式，資料是以哪種格式儲存對應用程式而言通常並不重要。  
  
 應用程式通常會提供多種序列化選項，以供使用者將文件儲存到不同媒體或不同格式。  例如，應用程式可能會提供 [另存新檔] 選項，以將文件儲存至磁碟檔案、資料庫或 Web 服務。  同樣地，不同序列化程式可能會將文件儲存成不同格式，例如 HTML、RTF、XML、XPS 或其他協力廠商格式。  對應用程式而言，序列化定義了一個介面，可將每個特定序列化程式實作時的儲存媒體詳細資料加以隔離。  除了將封裝儲存體的詳細資料的優點[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]提供數種重要的功能。  
  
### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 文件序列化程式的功能  
  
-   直接存取高階文件物件 (邏輯樹狀結構和視覺物件) 可以有效率地儲存分頁內容、2D/3D 項目、影像、媒體、超連結、註解和其他支援內容。  
  
-   同步和非同步作業。  
  
-   透過增強的功能支援外掛程式序列化程式：  
  
    -   供所有 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式使用的系統範圍存取權。  
  
    -   輕鬆探索應用程式外掛程式。  
  
    -   輕鬆部署、安裝和更新自訂的協力廠商外掛程式。  
  
    -   可支援自訂執行階段設定和選項的使用者介面。  
  
### <a name="xps-print-path"></a>XPS 列印路徑  
 Microsoft.NET Framework[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]列印路徑也會提供可擴充機制，用於撰寫透過列印輸出文件。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 可同時作為文件檔案格式，以及 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 的原生列印多工緩衝處理格式。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 文件可以直接傳送至 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 相容的印表機，而不需要轉換成中繼格式。  如需列印路徑輸出選項和功能的其他資訊，請參閱[列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)。  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>外掛程式序列化程式  
 <xref:System.Windows.Documents.Serialization> Api 提供之外掛程式序列化程式和連結的序列化程式從應用程式的獨立安裝的支援、 執行階段繫結和使用來存取<xref:System.Windows.Documents.Serialization.SerializerProvider>探索機制。  外掛程式序列化程式提供增強的優點，以便進行部署並在整個系統內使用。  在無法存取外掛程式序列化程式的部分信任環境中 (例如 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)])，也可以實作連結的序列化程式。  連結為基礎的衍生實作序列化程式<xref:System.Windows.Documents.Serialization.SerializerWriter>類別、 編譯和連結直接將應用程式。  外掛程式序列化程式和連結的序列化程式都是透過相同的公用方法和事件運作，因此您可以很輕易地在同一個應用程式中使用其中一種序列化程式 (或兩種都使用)。  
  
 外掛程式序列化程式可以協助應用程式開發人員擴充新的儲存設計和檔案格式，而不需要針對建置階段可能出現的每種格式直接撰寫程式碼。  外掛程式序列化程式同時也能夠提供協力廠商開發人員標準化的方法，來針對自訂或專屬檔案格式部署、安裝和更新可供系統存取的外掛程式。  
  
### <a name="using-a-plug-in-serializer"></a>使用外掛程式序列化程式  
 外掛程式序列化程式很容易使用。  <xref:System.Windows.Documents.Serialization.SerializerProvider>類別列舉<xref:System.Windows.Documents.Serialization.SerializerDescriptor>物件的系統上的每個外掛程式安裝。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A>屬性篩選依據目前的設定已安裝的外掛程式，並確認序列化程式可以載入，且應用程式使用。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor>也提供其他屬性，例如<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A>和<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>，應用程式可以用來提示使用者選取可用的輸出格式的序列化程式。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 的預設外掛程式序列化程式會隨 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 提供，而且一律會被列舉。  在使用者選取的輸出格式之後,<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>方法用來建立<xref:System.Windows.Documents.Serialization.SerializerWriter>特定格式。  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> 然後可以呼叫方法來輸出文件資料流資料存放區。  
  
 下列範例說明使用的應用程式<xref:System.Windows.Documents.Serialization.SerializerProvider>"PlugInFileFilter"屬性中的方法。  PlugInFileFilter 列舉已安裝的外掛程式和組建的可用檔案選項使用的篩選條件字串<xref:Microsoft.Win32.SaveFileDialog>。  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 已由使用者選取的輸出檔名稱之後，下列範例說明使用<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>方法來儲存給定文件中指定的格式。  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>安裝外掛程式序列化程式  
 <xref:System.Windows.Documents.Serialization.SerializerProvider>類別會提供外掛程式序列化程式探索及存取的上層應用程式介面。  <xref:System.Windows.Documents.Serialization.SerializerProvider> 找出並提供應用程式已安裝且可存取的系統上的序列化程式的清單。  已安裝之序列化程式的內容是透過登錄設定定義。  外掛程式序列化程式可以使用新增至登錄<xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A>方法; 或者如果[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]尚未安裝，安裝外掛程式指令碼可以直接設定登錄值本身。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A>方法可用來移除先前安裝外掛程式，或登錄設定可以來重設同樣解除安裝指令碼。  
  
### <a name="creating-a-plug-in-serializer"></a>建立外掛程式序列化程式  
 外掛程式序列化程式和連結的序列化程式使用已公開的相同公用方法和事件，而且同樣都能設計成以同步或非同步方式運作。  若要建立外掛程式序列化程式，通常要遵循三個基本步驟：  
  
1.  首先將序列化程式實作為連結的序列化程式並加以偵錯。  一開始就建立已編譯的序列化程式並將之直接連結到測試應用程式中，將可以完整存取中斷點和其他有助於進行測試的偵錯服務。  
  
2.  序列化程式會經過完整測試之後，<xref:System.Windows.Documents.Serialization.ISerializerFactory>介面會新增至建立外掛程式。  <xref:System.Windows.Documents.Serialization.ISerializerFactory>介面可讓您完整存取所有[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]物件，其中包含邏輯樹狀目錄中，<xref:System.Windows.UIElement>物件<xref:System.Windows.Documents.IDocumentPaginatorSource>，和<xref:System.Windows.Media.Visual>項目。  此外<xref:System.Windows.Documents.Serialization.ISerializerFactory>提供相同的同步和非同步方法和連結的序列化程式所使用的事件。  由於大型文件的輸出可能很費時，因此建議使用非同步作業，以維持與使用者的良好互動，並提供 [取消] 選項以防資料存放區發生問題。  
  
3.  建立外掛程式序列化程式之後，實作用於散發和安裝 (及解除安裝) 外掛程式的安裝指令碼 (請參閱上面的＜[安裝外掛程式序列化程式](#InstallingPluginSerializers)＞)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Paper Specification: Overview](http://go.microsoft.com/fwlink?LinkID=106246) (XML 文件規格︰概觀)
