---
title: XAML 服務
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
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 458b4c94d26b7bc083c5d31fcbccf05b42bba52e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-services"></a>XAML 服務
本主題描述技術集稱為.NET Framework XAML 服務的功能。 大部分的服務和應用程式開發介面所描述的位於 System.Xaml，也就是組件所導入的組件[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].NET core 組件集合。 服務包括讀取器和寫入器，結構描述類別和結構描述支援的處理站，設定其屬性的類別、 XAML 語言的內建支援和其他 XAML 語言功能。  
  
## <a name="about-this-documentation"></a>關於這份文件  
 .NET Framework XAML 服務的概念文件假設您有先前的經驗與 XAML 語言如何它可能會套用到特定的架構，例如[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]或[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]，或特定技術的功能區域中，範例中的組建自訂功能<xref:Microsoft.Build.Framework.XamlTypes>。 這份文件不會嘗試說明的基本概念的 XAML 標記語言、 XAML 語法術語中，或其他簡介資料。 相反地，本文件著重於特別使用 System.Xaml 組件的文件庫中的 已啟用.NET Framework XAML 服務。 大部分的這些 Api 會針對 XAML 語言整合和擴充性案例。 這可能包括下列任何一項：  
  
-   擴充的基底的 XAML 讀取器或 XAML 寫入器 （直接處理 XAML 節點資料流; 衍生您自己的 XAML 讀取器或 XAML 寫入器） 的功能。  
  
-   定義，並沒有特定架構相依性，可使用 XAML 自訂型別，並設定其屬性的型別來傳達其 XAML 輸入.NET Framework XAML 服務的系統特性。  
  
-   裝載的 XAML 讀取器或 XAML 寫入器，為應用程式，例如視覺化設計工具或互動式 XAML 標記來源編輯器的元件。  
  
-   撰寫 XAML 值轉換器 （標記延伸，類型轉換器的自訂型別）。  
  
-   定義自訂的 XAML 結構描述內容 (使用替代的組件載入技術來備份類型的來源，而不永遠使用已知型別查閱技術反映組件，才能使用; 不是使用 CLR 載入的組件概念`AppDomain`和其相關聯的安全性模型）。  
  
-   擴充的基底的 XAML 類型系統。  
  
-   使用`Lookup`或`Invoker`技術來影響 XAML 類型系統，以及如何評估類型 backings 的。  
  
 如果您要尋找的 XAML 語言的簡介資料，您可能會嘗試[XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。 該主題討論 XAML。 新的對象， [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ，也可以使用 XAML 標記和 XAML 語言功能。 另一個有用的文件是在簡介資料[XAML 語言規格](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML 服務和 System.Xaml 中的.NET 架構  
 在舊版的[!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)]，支援 XAML 語言功能實作的架構上建置[!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]，[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]和[!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)])，並因此改變其行為和依據所用的 API您已使用特定的架構。 這包含 XAML 剖析器和它的物件圖形建立機制、 XAML 語言內建函式、 序列化支援等等。  
  
 在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，.NET Framework XAML 服務和 System.Xaml 組件定義大部分的所需的支援 XAML 語言功能。 這包括基底類別的 XAML 讀取器和 XAML 寫入器。 加入未出現在任何架構特定 XAML 實作的.NET Framework XAML 服務最重要功能是 xaml 類型系統表示法。 類型系統表示法呈現 XAML 著重的 XAML 功能但不採取特定功能的架構相依性物件導向的方式。  
  
 XAML 類型系統不受限於標記形式或執行階段特性 XAML 來源。也不它受到任何特定的支援類型系統。 XAML 類型系統中包含類型、 成員、 XAML 結構描述內容、 XML 層級概念，和其他 XAML 語言概念或 XAML 內建函式的物件表示的法。 使用或擴充 XAML 類型系統可讓衍生自類別，例如 XAML 讀取器和 XAML 寫入器，並擴充到啟用的架構、 技術或使用應用程式的特定功能的 XAML 表示的功能或會發出 XAML。 XAML 結構描述內容的概念可讓您從 XAML 物件寫入器實作，因為通訊透過內容和 XAML 節點中的組件資訊的技術支援類型系統的組合的實際物件圖形寫入操作來源。 如需 XAML 結構描述概念的詳細資訊。 請參閱[預設 XAML 結構描述內容和 WPF XAML 結構描述內容](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md)。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML 節點資料流，XAML 讀取器和 XAML 寫入器  
 若要了解.NET Framework XAML 服務 XAML 語言並使用 XAML 語言的特定技術之間的關聯性中所扮演的角色，最好先了解在 XAML 節點資料流和該概念如何圖形 API 的概念和術語。 XAML 節點資料流是 XAML 語言表示法與 XAML 表示，或定義的物件圖形之間的概念中繼。  
  
-   XAML 讀取器是處理某種形式的 XAML 和產生 XAML 節點資料流的實體。 在 API 中，XAML 讀取器由基底類別<xref:System.Xaml.XamlReader>。  
  
-   XAML 寫入器是處理 XAML 節點資料流和其他項目產生的實體。 在 API 中，XAML 寫入器由基底類別<xref:System.Xaml.XamlWriter>。  
  
 XAML 牽涉到兩個最常見的案例會載入 XAML 物件圖形，具現化和儲存物件圖形中的應用程式或工具，並產生 （通常是在標記形式儲存為文字檔案） 的 XAML 表示法。 載入 XAML，和建立物件圖形通常稱為本文件的載入路徑中。 儲存或序列化為 XAML 的現有物件圖形通常指在這份文件儲存為路徑。  
  
 最常見的載入路徑類型描述如下：  
  
-   XAML 表示，格式為 UTF-16 編碼的 XML 開始，並儲存為文字檔案。  
  
-   到該 XAML 載入<xref:System.Xaml.XamlXmlReader>。 <xref:System.Xaml.XamlXmlReader>是<xref:System.Xaml.XamlReader>子類別。  
  
-   結果是在 XAML 節點資料流。 您可以存取個別節點的 XAML 節點資料流使用<xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader>應用程式開發介面。 最常見的作業是在 XAML 節點資料流，處理每個節點使用 「 目前的記錄 」 中向前推進比喻。  
  
-   產生的節點傳遞至 XAML 節點資料流從<xref:System.Xaml.XamlObjectWriter>應用程式開發介面。 <xref:System.Xaml.XamlObjectWriter>是<xref:System.Xaml.XamlWriter>子類別。  
  
-   <xref:System.Xaml.XamlObjectWriter>像素來進行來源 XAML 節點資料流寫入物件圖形中，一次一個物件。 這是與 XAML 結構描述內容和實作的組件和支援類型系統和 framework 型別可存取的協助。  
  
-   呼叫<xref:System.Xaml.XamlObjectWriter.Result%2A>XAML 節點資料流，以取得物件圖形的根物件的結尾。  
  
 最常見的類型儲存路徑描述如下：  
  
-   物件圖形的整個執行的應用程式時間、 UI 內容和狀態的執行階段或在執行階段的整體應用程式的物件表示的較小區段的開頭。  
  
-   從邏輯開始物件，例如應用程式根目錄或文件根物件載入<xref:System.Xaml.XamlObjectReader>。 <xref:System.Xaml.XamlObjectReader>是<xref:System.Xaml.XamlReader>子類別。  
  
-   結果是在 XAML 節點資料流。 您可以存取個別節點的 XAML 節點資料流使用<xref:System.Xaml.XamlObjectReader>和<xref:System.Xaml.XamlReader>應用程式開發介面。 最常見的作業是在 XAML 節點資料流，處理每個節點使用 「 目前的記錄 」 中向前推進比喻。  
  
-   產生的節點傳遞至 XAML 節點資料流從<xref:System.Xaml.XamlXmlWriter>應用程式開發介面。 <xref:System.Xaml.XamlXmlWriter>是<xref:System.Xaml.XamlWriter>子類別。  
  
-   <xref:System.Xaml.XamlXmlWriter> XAML 寫入 XML utf 編碼方式。 您可以將它儲存為資料流、 或其他形式的文字檔案。  
  
-   呼叫<xref:System.Xaml.XamlXmlWriter.Flush%2A>取得最終輸出。  
  
 如需 XAML 節點資料流概念的詳細資訊，請參閱[了解 XAML 節點資料流結構和概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
### <a name="the-xamlservices-class"></a>XamlServices 類別  
 您不一定需要處理 XAML 節點資料流。 如果您要將基本的載入路徑或儲存路徑的基本，您可以使用應用程式開發介面中的<xref:System.Xaml.XamlServices>類別。  
  
-   不同的簽章<xref:System.Xaml.XamlServices.Load%2A>實作載入路徑。 您可以載入檔案或資料流，或可以載入<xref:System.Xml.XmlReader>，<xref:System.IO.TextReader>或<xref:System.Xaml.XamlReader>，與該讀取器 Api 一起載入時用來包裝您的 XAML 輸入。  
  
-   不同的簽章<xref:System.Xaml.XamlServices.Save%2A>儲存物件圖形，並產生輸出資料流、 檔案，或<xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter>執行個體。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A>將 XAML 轉換藉由將載入路徑和儲存連結成單一作業的路徑。 不同的結構描述內容或支援類型系統無法用於<xref:System.Xaml.XamlReader>和<xref:System.Xaml.XamlWriter>，這是影響產生之 XAML 的轉換方式。  
  
 如需有關如何使用<xref:System.Xaml.XamlServices>，請參閱[XAMLServices 類別和基本 XAML 讀取或寫入](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md)。  
  
## <a name="xaml-type-system"></a>XAML 類型系統  
 XAML 類型系統會提供用於指定的個別節點的 XAML 節點資料流所需的 Api。  
  
 <xref:System.Xaml.XamlType>是一個物件的表示您正在處理的開始物件節點和結束物件節點之間。  
  
 <xref:System.Xaml.XamlMember>為成員的物件-表示您正在處理的開始成員節點和結束成員節點之間。  
  
 應用程式開發介面，例如<xref:System.Xaml.XamlType.GetAllMembers%2A>和<xref:System.Xaml.XamlType.GetMember%2A>和<xref:System.Xaml.XamlMember.DeclaringType%2A>報表之間的關聯性<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>。  
  
 由.NET Framework XAML 服務實作時，XAML 類型系統的預設行為根據 common language runtime (CLR) 和組件中的 CLR 類型的靜態分析使用反映。 因此，對於特定的 CLR 類型，XAML 類型系統的預設實作可以公開該類型和其成員的 XAML 結構描述，並報告方面 XAML 類型系統。 在預設 XAML 類型系統中的指派性類型的概念對應到 CLR 繼承和執行個體、 實值類型等等的概念也對應至支援的行為和的 CLR 功能。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 語言功能的參考  
 若要支援 XAML，.NET Framework XAML 服務提供 XAML 語言概念為 XAML 語言 XAML 命名空間所定義的特定的實作。 這些案例記載為特定的參考頁面。 語言功能會記錄觀點的 XAML 讀取器或所定義的.NET Framework XAML 服務 XAML 寫入器處理時，這些語言功能的行為方式。 如需詳細資訊，請參閱 [XAML Namespace (x:) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。
