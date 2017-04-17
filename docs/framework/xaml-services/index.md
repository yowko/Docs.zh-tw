---
title: "XAML Services | Microsoft Docs"
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
  - "XAML [XAML Services], System.Xaml concepts"
  - "XAML Services in WPF [XAML Services]"
  - "System.Xaml [XAML Services], conceptual documentation"
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XAML Services
本主題說明名為 .NET Framework XAML 服務之技術集的功能。  文中所說明的大部分服務與 API 位於組件 System.Xaml 中，此為 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的 .NET 核心組件集隨附的組件。  服務包括讀取器和寫入器、結構描述類別和結構描述支援、Factory、類別屬性、XAML 語言本質支援，和其他 XAML 語言功能。  
  
## 關於本文件  
 這是 .NET Framework XAML 服務的概念文件，文中假設您先前體驗過 XAML 語言、它如何套用至特定架構 \(例如 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 或 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]\)，或是特定技術功能領域 \(例如 <xref:Microsoft.Build.Framework.XamlTypes> 中的自訂建置功能\)。  本文件不會嘗試說明 XAML 的基本標記語言概念、XAML 語法用語，或其他簡介資料。  但是，本文件會特別著重在使用以 System.Xaml 組件程式庫啟用的 .NET Framework XAML 服務。  其中大部分的 API 適用於 XAML 語言的整合與擴充情節。  其中可能包含下列情節：  
  
-   擴充基底 XAML 讀取器或 XAML 寫入器的功能 \(直接處理 XAML 節點資料流；衍生您自己的 XAML 讀取器或 XAML 寫入器\)。  
  
-   定義適用於 XAML 而不具特定架構相依性的自訂型別，並設定型別的屬性，以將其 XAML 型別系統特性傳送至 .NET Framework XAML 服務。  
  
-   將 XAML 讀取器或 XAML 寫入器裝載為應用程式的元件，例如適用於 XAML 標記來源的視覺化設計工具或互動式編輯器。  
  
-   撰寫 XAML 值轉換器 \(標記延伸；自訂型別的型別轉換器\)。  
  
-   定義自訂 XAML 結構描述內容 \(對支援型別來源使用替代組件載入技術；使用已知型別的查閱技術，而非一律反映組件；使用未使用 CLR `AppDomain` 及其相關安全性模型的載入組件概念\)。  
  
-   擴充基底 XAML 型別系統。  
  
-   使用 `Lookup` 或 `Invoker` 技術影響 XAML 型別系統以及型別支援的評估方式。  
  
 如果您要尋找 XAML 語言簡介資料，請參閱 [XAML 概觀 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)。  該主題會為不熟悉 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 以及初次使用 XAML 標記和 XAML 語言功能的讀者討論 XAML。  其他有用的文件是 [XAML 語言規格](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\) 中的簡介資料。  
  
## .NET 架構中的 .NET Framework XAML 服務與 System.Xaml  
 在舊版 [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] 中，XAML 語言功能的支援是由建置在 [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] \([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] 和 [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]\) 上的架構實作，因此表現出的行為各異，而且使用的 API 會因您使用的特定架構而有所不同。  這包括 XAML 剖析器及其物件圖形建立機制、XAML 語言本質、序列化支援等等。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，.NET Framework XAML 服務與 System.Xaml 組件定義了許多支援 XAML 語言功能所需的項目。  這包括 XAML 讀取器和 XAML 寫入器的基底類別。  .NET Framework XAML 服務中加入了一項以往架構特有 XAML 實作所沒有的重要功能，就是 XAML 的型別系統表示。  型別系統表示可透過以 XAML 功能為中心的物件導向方式呈現 XAML，而無須依存於特定的架構功能。  
  
 XAML 型別系統不受限於 XAML 出處的標記表單或執行階段特性，亦不受限於特定支援型別系統。  XAML 型別系統包含型別、成員、XAML 結構描述內容、XML 層級概念，和其他 XAML 語言概念或 XAML 本質的物件表示。  藉由使用或擴充 XAML 型別系統，將可以從像是 XAML 讀取器和 XAML 寫入器的類別衍生，並且將 XAML 表示的功能 \(Functionality\) 擴充成由會使用或發出 XAML 的架構、技術或應用程式所啟用的特定功能。  XAML 結構描述內容的概念可讓您結合下列三個項目，以執行實際的物件圖形寫入作業：XAML 物件寫入器實作、技術的支援型別系統 \(在透過內容中的組件資訊通訊時\)、以及 XAML 節點來源。  如需 XAML 結構描述概念的詳細資訊，  請參閱 [Default XAML Schema Context and WPF XAML Schema Context](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md)。  
  
## XAML 節點資料流、XAML 讀取器和 XAML 寫入器  
 若要了解 .NET Framework XAML 服務在 XAML 語言和使用 XAML 語言的特定技術之間的關聯性所扮演的角色，先了解 XAML 節點資料流的概念，以及如何以此概念形成 API 和詞彙，將會很有幫助。  XAML 節點資料流是 XAML 語言表示和該 XAML 所表示或定義之物件圖形之間的概念性中繼項目。  
  
-   XAML 讀取器是實體，它會以某種形式處理 XAML，然後產生 XAML 節點資料流。  在 API 中，XAML 讀取器由基底類別 <xref:System.Xaml.XamlReader> 表示。  
  
-   XAML 寫入器是實體，它會處理 XAML 節點資料流，然後產生其他形式的輸出。  在 API 中，XAML 寫入器由基底類別 <xref:System.Xaml.XamlWriter> 表示。  
  
 與 XAML 有關的兩個最常見的情節就是載入 XAML 來執行個體化物件圖形，以及從應用程式或工具儲存物件圖形然後產生 XAML 表示 \(通常是以文字檔形式儲存的標記\)。  載入 XAML 然後建立物件圖形的動作，在本文件中通常稱為載入路徑。  將現有物件圖形儲存或序列化為 XAML 的動作，在本文件中通常稱為儲存路徑。  
  
 最常見的載入路徑類型如下所述：  
  
-   從 XAML 表示開始，這個 XAML 表示是 UTF 編碼 XML 格式，以文字檔形式儲存。  
  
-   將該 XAML 載入至 <xref:System.Xaml.XamlXmlReader> 中。  <xref:System.Xaml.XamlXmlReader> 是 <xref:System.Xaml.XamlReader> 的子類別。  
  
-   結果產生 XAML 節點資料流。  您可以使用 <xref:System.Xaml.XamlXmlReader> \/ <xref:System.Xaml.XamlReader> API 存取 XAML 節點資料流的個別節點。  這裡最典型的作業是藉由使用「目前記錄」比喻處理每個節點，在 XAML 節點資料流中逐步前進。  
  
-   將從 XAML 節點資料流產生的節點傳遞給 <xref:System.Xaml.XamlObjectWriter> API。  <xref:System.Xaml.XamlObjectWriter> 是 <xref:System.Xaml.XamlWriter> 的子類別。  
  
-   <xref:System.Xaml.XamlObjectWriter> 藉由根據在來源 XAML 節點資料流中的進度一次寫下一個物件，來撰寫物件圖形。  這是在兩個項目的輔助下完成：XAML 結構描述內容，和可存取備份型別系統和架構中之組件和型別的實作。  
  
-   在 XAML 節點資料流結尾呼叫 <xref:System.Xaml.XamlObjectWriter.Result%2A>，以取得物件圖形的根物件。  
  
 最常見的儲存路徑類型如下所述：  
  
-   從整個應用程式執行階段的物件圖形、執行階段的 UI 內容和狀態，或是整個應用程式物件表示在執行階段的一個小區段開始。  
  
-   從某個邏輯起始物件 \(例如應用程式根目錄或文件根目錄\) 開始載入物件至 <xref:System.Xaml.XamlObjectReader> 中。  <xref:System.Xaml.XamlObjectReader> 是 <xref:System.Xaml.XamlReader> 的子類別。  
  
-   結果產生 XAML 節點資料流。  您可以使用 <xref:System.Xaml.XamlObjectReader> 和 <xref:System.Xaml.XamlReader> API 存取 XAML 節點資料流的個別節點。  這裡最典型的作業是藉由使用「目前記錄」比喻處理每個節點，在 XAML 節點資料流中逐步前進。  
  
-   將從 XAML 節點資料流產生的節點傳遞給 <xref:System.Xaml.XamlXmlWriter> API。  <xref:System.Xaml.XamlXmlWriter> 是 <xref:System.Xaml.XamlWriter> 的子類別。  
  
-   <xref:System.Xaml.XamlXmlWriter> 以 XML UTF 編碼撰寫 XAML。  您可以將這儲存為文字檔、資料流或其他格式。  
  
-   呼叫 <xref:System.Xaml.XamlXmlWriter.Flush%2A> 以取得最終輸出。  
  
 如需 XAML 節點資料流概念的詳細資訊，請參閱[Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
### XamlServices 類別  
 您不一定要處理 XAML 節點資料流。  如果您要基本的載入路徑或基本的儲存路徑，可以使用 <xref:System.Xaml.XamlServices> 類別中的 API。  
  
-   <xref:System.Xaml.XamlServices.Load%2A> 的各種簽章會實作載入路徑。  您可以載入檔案或資料流，也可以載入 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader> 或 <xref:System.Xaml.XamlReader>，藉由與該讀取器的 API 一起載入以包裝您的 XAML 輸入。  
  
-   <xref:System.Xaml.XamlServices.Save%2A> 的各種簽章會儲存物件圖形，然後輸出資料流、檔案或 <xref:System.Xml.XmlWriter>\/<xref:System.IO.TextWriter> 執行個體。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> 會藉由將載入路徑和儲存路徑連結成單一作業，以轉換 XAML。  <xref:System.Xaml.XamlReader> 和 <xref:System.Xaml.XamlWriter> 則可能會使用不同的結構描述內容或備份型別系統，而這正是影響 XAML 轉換結果的因素。  
  
 如需如何使用 <xref:System.Xaml.XamlServices>的詳細資訊，請參閱[XAMLServices Class and Basic XAML Reading or Writing](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md)。  
  
## XAML 型別系統  
 XAML 型別系統提供處理 XAML 節點資料流中的某個特定節點所需的 API。  
  
 <xref:System.Xaml.XamlType> 是物件的表示 \- 您會處理在起始物件節點和結束物件節點之間的內容。  
  
 <xref:System.Xaml.XamlMember> 是物件成員的表示 \- 您會處理在起始成員節點和結束成員節點之間的內容。  
  
 <xref:System.Xaml.XamlType.GetAllMembers%2A> 和 <xref:System.Xaml.XamlType.GetMember%2A> 等這些 API 以及 <xref:System.Xaml.XamlMember.DeclaringType%2A> 會報告 <xref:System.Xaml.XamlType> 和 <xref:System.Xaml.XamlMember> 之間的關聯性。  
  
 .NET Framework XAML 服務所實作之 XAML 型別系統的預設行為，是以 Common Language Runtime \(CLR\) 以及針對組件中的 CLR 型別使用反映進行的靜態分析為根據。  因此，對於特定 CLR 型別，預設實作的 XAML 型別系統可以公開該型別的 XAML 結構描述和其成員，並且以 XAML 型別系統的觀點加以報告。  在預設 XAML 型別系統中，型別的可指派性概念是對應至 CLR 繼承，而執行個體、值型別等等的概念也對應至 CLR 的支援行為和功能。  
  
## XAML 語言功能的參考資料  
 為支援 XAML，.NET Framework XAML 服務提供了針對 XAML 語言 XAML 命名空間而定義之 XAML 語言概念的特定實作方式。  這些資訊分別記載於特定的參考頁面。  語言功能的相關參考資料，會從這些語言功能由 .NET Framework XAML 服務所定義的 XAML 讀取器或 XAML 寫入器處理時會有哪些行為的觀點來說明。  如需詳細資訊，請參閱 [XAML Namespace \(x:\) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。