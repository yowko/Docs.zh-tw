---
title: 文件序列化與儲存
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 7ddd887eefd67a3300795396dac26e855f30989e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254115"
---
# <a name="document-serialization-and-storage"></a>文件序列化與儲存

Microsoft .NET Framework 提供強大的環境來建立和顯示高品質的檔。  同時支援固定檔和流程檔、先進的視圖控制項以及強大的2D 和3D 圖形功能的增強功能, 可讓 .NET Framework 的應用程式獲得新的品質和使用者體驗。  能夠以彈性的方式管理檔的記憶體內部表示是 .NET Framework 的主要功能, 而且能夠有效率地儲存和載入資料存放區中的檔是幾乎每個應用程式的需求。  將文件從記憶體內部表示轉換成外部資料存放區的程序，稱為序列化。  讀取資料存放區並重新建立原始記憶體內部執行個體的反向程序，則稱為還原序列化。

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>關於文件序列化

在理想情況下，與記憶體之間進行的文件序列化和還原序列化程序，對於應用程式而言是透明的。  應用程式會呼叫序列化程式的 "write" 方法來儲存文件，而還原序列化程式的 "read" 方法則會存取資料存放區並在記憶體中重新建立原始執行個體。  只要序列化和還原序列化程序會將文件重新建立成原始格式，資料是以哪種格式儲存對應用程式而言通常並不重要。

應用程式通常會提供多種序列化選項，以供使用者將文件儲存到不同媒體或不同格式。  例如，應用程式可能會提供 [另存新檔] 選項，以將文件儲存至磁碟檔案、資料庫或 Web 服務。  同樣地，不同序列化程式可能會將文件儲存成不同格式，例如 HTML、RTF、XML、XPS 或其他協力廠商格式。  對應用程式而言，序列化定義了一個介面，可將每個特定序列化程式實作時的儲存媒體詳細資料加以隔離。  除了封裝儲存體詳細資料的優點之外, .NET Framework <xref:System.Windows.Documents.Serialization> api 還提供其他幾項重要功能。

### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 文件序列化程式的功能

- 直接存取高階文件物件 (邏輯樹狀結構和視覺物件) 可以有效率地儲存分頁內容、2D/3D 項目、影像、媒體、超連結、註解和其他支援內容。

- 同步和非同步作業。

- 透過增強的功能支援外掛程式序列化程式：

  - 所有 .NET Framework 應用程式都可使用整個系統的存取權。

  - 輕鬆探索應用程式外掛程式。

  - 輕鬆部署、安裝和更新自訂的協力廠商外掛程式。

  - 可支援自訂執行階段設定和選項的使用者介面。

### <a name="xps-print-path"></a>XPS 列印路徑

Microsoft .NET Framework XPS 列印路徑也提供可擴充的機制, 可透過列印輸出寫入檔。  XPS 可同時做為檔檔格式, 而且是的原生列印多[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]任務緩衝處理格式。  XPS 檔可以直接傳送到與 XPS 相容的印表機, 而不需要轉換成中繼格式。  如需列印路徑輸出選項和功能的其他資訊，請參閱[列印概觀](printing-overview.md)。

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>外掛程式序列化程式

這些<xref:System.Windows.Documents.Serialization> api 同時支援外掛程式序列化程式和連結的序列化程式, 這些是與應用程式分開安裝、在執行時間進行系結, 並<xref:System.Windows.Documents.Serialization.SerializerProvider>使用探索機制來存取。  外掛程式序列化程式提供增強的優點，以便進行部署並在整個系統內使用。  在無法存取外掛程式序列化程式的部分信任環境中 (例如 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)])，也可以實作連結的序列化程式。  連結的序列化程式是以<xref:System.Windows.Documents.Serialization.SerializerWriter>類別的衍生實作為基礎, 會進行編譯並直接連結到應用程式。  外掛程式序列化程式和連結的序列化程式都是透過相同的公用方法和事件運作，因此您可以很輕易地在同一個應用程式中使用其中一種序列化程式 (或兩種都使用)。

外掛程式序列化程式可以協助應用程式開發人員擴充新的儲存設計和檔案格式，而不需要針對建置階段可能出現的每種格式直接撰寫程式碼。  外掛程式序列化程式同時也能夠提供協力廠商開發人員標準化的方法，來針對自訂或專屬檔案格式部署、安裝和更新可供系統存取的外掛程式。

### <a name="using-a-plug-in-serializer"></a>使用外掛程式序列化程式

外掛程式序列化程式很容易使用。  類別會列舉系統上所安裝之每個外掛程式的物件。<xref:System.Windows.Documents.Serialization.SerializerDescriptor> <xref:System.Windows.Documents.Serialization.SerializerProvider>  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A>屬性會根據目前的設定篩選已安裝的外掛程式, 並確認應用程式可以載入及使用序列化程式。  也提供其他屬性 ( <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A>例如和<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>), 應用程式可以使用它們來提示使用者選取可用輸出格式的序列化程式。 <xref:System.Windows.Documents.Serialization.SerializerDescriptor>  XPS 的預設外掛程式序列化程式會隨 .NET Framework 一起提供, 而且一律會列舉。  在使用者選取輸出格式之後, <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>會使用方法來<xref:System.Windows.Documents.Serialization.SerializerWriter>建立特定格式的。  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> 然後可以呼叫方法, 將檔資料流程輸出至資料存放區。

下列範例說明在 "PlugInFileFilter" 屬性中<xref:System.Windows.Documents.Serialization.SerializerProvider>使用方法的應用程式。  PlugInFileFilter 會列舉已安裝的外掛程式, 並使用的可用檔案選項來<xref:Microsoft.Win32.SaveFileDialog>建立篩選字串。

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

使用者選取輸出檔名稱之後, 下列範例會示範如何使用<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>方法, 以指定的格式儲存給定的檔。

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>安裝外掛程式序列化程式

<xref:System.Windows.Documents.Serialization.SerializerProvider>類別會提供外掛程式序列化程式探索和存取的上層應用程式介面。  <xref:System.Windows.Documents.Serialization.SerializerProvider>找出並提供應用程式清單, 列出系統上已安裝和可存取的序列化程式。  已安裝之序列化程式的內容是透過登錄設定定義。  外掛程式序列化程式可以使用<xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A>方法新增到登錄中; 或者, 如果尚未安裝 .NET Framework, 外掛程式安裝腳本就可以直接設定登錄值本身。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A>方法可用來移除先前安裝的外掛程式, 或使用卸載腳本來重設登錄設定。

### <a name="creating-a-plug-in-serializer"></a>建立外掛程式序列化程式

外掛程式序列化程式和連結的序列化程式使用已公開的相同公用方法和事件，而且同樣都能設計成以同步或非同步方式運作。  若要建立外掛程式序列化程式，通常要遵循三個基本步驟：

1. 首先將序列化程式實作為連結的序列化程式並加以偵錯。  一開始就建立已編譯的序列化程式並將之直接連結到測試應用程式中，將可以完整存取中斷點和其他有助於進行測試的偵錯服務。

2. 在序列化程式經過完整測試之後, <xref:System.Windows.Documents.Serialization.ISerializerFactory>就會加入介面來建立外掛程式。  介面允許包含邏輯樹狀結構、 <xref:System.Windows.UIElement>物件、 <xref:System.Windows.Documents.IDocumentPaginatorSource>和<xref:System.Windows.Media.Visual>專案的所有 .NET Framework 物件的完整存取權。 <xref:System.Windows.Documents.Serialization.ISerializerFactory>  此外<xref:System.Windows.Documents.Serialization.ISerializerFactory> , 也提供連結序列化程式所使用的相同同步和非同步方法和事件。  由於大型文件的輸出可能很費時，因此建議使用非同步作業，以維持與使用者的良好互動，並提供 [取消] 選項以防資料存放區發生問題。

3. 建立外掛程式序列化程式之後，實作用於散發和安裝 (及解除安裝) 外掛程式的安裝指令碼 (請參閱上面的＜[安裝外掛程式序列化程式](#InstallingPluginSerializers)＞)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [XML 檔規格:概觀](https://go.microsoft.com/fwlink?LinkID=106246)
