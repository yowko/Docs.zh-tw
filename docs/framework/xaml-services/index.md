---
title: XAML 服務
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 373478e8c21fca66cbfbf7a58fc7d53f65ce5d0b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195095"
---
# <a name="xaml-services"></a>XAML 服務
本主題說明的技術集合，稱為.NET Framework XAML 服務的功能。 大部分的服務和描述 Api 位於 System.Xaml，這是組件所引進的組件[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]的.NET core 組件集。 服務包括讀取器和寫入，結構描述類別和結構描述支援的處理站，設定其屬性的類別、 XAML 語言內建支援和其他 XAML 語言功能。  
  
## <a name="about-this-documentation"></a>了解此文件  
 .NET Framework XAML 服務的概念文件假設您有先前的 XAML 語言以及如何它可能會套用至特定的架構，例如體驗[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Workflow Foundation 中或特定技術功能區域中，例如組建自訂中的功能<xref:Microsoft.Build.Framework.XamlTypes>。 這份文件不會嘗試為標記語言、 XAML 語法術語中或其他簡介教材說明 XAML 的基本概念。 相反地，這份文件著重於特別使用 System.Xaml 組件的文件庫中的 已啟用.NET Framework XAML 服務。 這些 Api 大部分都是 XAML 語言整合與擴充性案例。 這可能包括下列其中一項：  
  
-   擴充的基底的 XAML 讀取器或 XAML 寫入器 （直接處理 XAML 節點資料流; 衍生您自己的 XAML 讀取器或 XAML 寫入器） 的功能。  
  
-   定義，並沒有特定架構相依性，可使用 XAML 自訂型別和屬性的型別來傳達其 XAML 類型系統特性，以.NET Framework XAML 服務。  
  
-   裝載的應用程式，例如視覺化設計工具或 XAML 標記來源的互動式編輯器元件的 XAML 讀取器或 XAML 寫入器。  
  
-   撰寫 XAML 值轉換器 （標記延伸，類型轉換器的自訂型別）。  
  
-   定義自訂的 XAML 結構描述內容 (使用替代的組件載入技術來支援型別來源; 使用已知型別查閱技術，而不永遠反映組件，使用載入的組件的概念，請勿使用 CLR`AppDomain`和其相關聯的安全性模型）。  
  
-   擴充的基底的 XAML 類型系統。  
  
-   使用`Lookup`或`Invoker`技術，以影響 XAML 型別系統和型別 backings 的評估方式。  
  
 如果您要尋找在 XAML 做為語言的簡介教材，您可以試試[XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。 該主題討論 XAML 的新功能的對象來[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]以及使用 XAML 標記和 XAML 語言功能。 另一個有用的文件是在簡介教材[XAML 語言規格](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML 服務和 System.Xaml 中的.NET 架構  
 在舊版的 Microsoft.NET Framework 中，對 XAML 語言功能實作的 Microsoft.NET Framework 建置的架構支援 ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]，Windows Workflow Foundation 和 Windows Communication Foundation (WCF))，因此其行為和 API 所使用的特定架構根據您所使用的各不相同。 這包含 XAML 剖析器和其物件圖形建立機制、 XAML 語言內建函式、 序列化支援等等。  
  
 在  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，.NET Framework XAML 服務和 System.Xaml 組件定義大部分所需的支援 XAML 語言功能。 這可以包括基底類別的 XAML 讀取器和 XAML 寫入器。 加入不存在於任何架構特定 XAML 實作的.NET Framework XAML 服務的最重要功能是針對 XAML 類型系統表示法。 類型系統表示法呈現 XAML 著重 XAML 功能，但不採取相依性的架構的特定功能以物件導向的方式。  
  
 XAML 類型系統不受限於標記形式或 XAML 原點; 的執行階段特性也不它受到任何特定的支援型別系統。 XAML 類型系統包含類型、 成員、 XAML 結構描述的內容，XML 層級概念，和其他 XAML 語言概念或 XAML 內建函式的物件的表示。 使用或擴充的 XAML 型別系統可讓您從 XAML 讀取器和 XAML 寫入器，例如類別衍生並擴充到啟用的一種架構、 一種技術或使用應用程式的特定功能的 XAML 表示的功能或XAML 就會發出。 XAML 結構描述內容的概念可讓 XAML 物件寫入器實作，因為通訊透過內容和 XAML 節點中的組件資訊的技術支援型別系統的組合的實際物件 graph 寫入作業來源。 如需有關 XAML 結構描述概念的詳細資訊。 請參閱[預設 XAML 結構描述內容和 WPF XAML 結構描述內容](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md)。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML 節點資料流，XAML 讀取器和 XAML 寫入器  
 若要了解.NET Framework XAML 服務 XAML 語言和 XAML 作為語言的特定技術之間的關聯性中所扮演的角色，最好先了解的概念，XAML 節點資料流，以及該概念圖形 API 的方式和術語。 XAML 節點資料流是 XAML 語言表示法與 XAML 表示，或定義的物件圖形之間的概念中繼。  
  
-   XAML 讀取器是處理某種形式的 XAML，並產生 XAML 節點資料流的實體。 在 API 中，XAML 讀取器由基底類別<xref:System.Xaml.XamlReader>。  
  
-   XAML 寫入器是一個實體來處理 XAML 節點資料流，並會產生其他項目。 在 API 中，XAML 寫入器由基底類別<xref:System.Xaml.XamlWriter>。  
  
 涉及 XAML 的兩個最常見案例是載入 XAML 來具現化物件圖形，並從應用程式或工具中儲存的物件圖形並產生 （通常是在儲存為文字檔的標記形式） 的 XAML 表示。 載入 XAML，和建立物件圖形通常就是在載入路徑本文件集中。 儲存或序列化 XAML 至現有的物件圖形通常指在另存為這份文件路徑。  
  
 最常見的載入路徑的類型說明如下：  
  
-   開始使用的 XAML 表示法，以 UTF 編碼的 XML 格式，並儲存為文字檔。  
  
-   載入至該 XAML <xref:System.Xaml.XamlXmlReader>。 <xref:System.Xaml.XamlXmlReader> 是<xref:System.Xaml.XamlReader>子類別。  
  
-   結果是 XAML 節點資料流。 您可以存取的 XAML 節點資料流使用的個別節點<xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API。 最常見的作業為 XAML 節點資料流處理使用 「 目前的記錄 」 的每個節點中向前推進比喻。  
  
-   將 XAML 節點資料流傳遞產生的節點<xref:System.Xaml.XamlObjectWriter>API。 <xref:System.Xaml.XamlObjectWriter> 是<xref:System.Xaml.XamlWriter>子類別。  
  
-   <xref:System.Xaml.XamlObjectWriter>根據來源 XAML 節點資料流進行寫入物件圖形，一次的一個物件。 這是 XAML 結構描述內容和可存取組件和類型的支援型別系統和 framework 實作的協助。  
  
-   呼叫<xref:System.Xaml.XamlObjectWriter.Result%2A>XAML 節點資料流，以取得物件圖形的根物件的結尾。  
  
 最常見的類型儲存路徑可以如下所述：  
  
-   物件圖形的整個應用程式執行時間、 UI 內容和狀態的執行階段中或在執行階段的整體應用程式的物件表示的較小區段的開頭。  
  
-   從邏輯開始物件，例如應用程式的根目錄或文件根物件載入至<xref:System.Xaml.XamlObjectReader>。 <xref:System.Xaml.XamlObjectReader> 是<xref:System.Xaml.XamlReader>子類別。  
  
-   結果是 XAML 節點資料流。 您可以存取的 XAML 節點資料流使用的個別節點<xref:System.Xaml.XamlObjectReader>和<xref:System.Xaml.XamlReader>API。 最常見的作業為 XAML 節點資料流處理使用 「 目前的記錄 」 的每個節點中向前推進比喻。  
  
-   將 XAML 節點資料流傳遞產生的節點<xref:System.Xaml.XamlXmlWriter>API。 <xref:System.Xaml.XamlXmlWriter> 是<xref:System.Xaml.XamlWriter>子類別。  
  
-   <xref:System.Xaml.XamlXmlWriter> XAML 寫入 XML utf 編碼。 您可以將它儲存為文字檔案，做為資料流，或其他格式。  
  
-   呼叫<xref:System.Xaml.XamlXmlWriter.Flush%2A>取得最終輸出。  
  
 如需有關 XAML 節點資料流概念的詳細資訊，請參閱 <<c0> [ 了解 XAML 節點 Stream 結構和概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
### <a name="the-xamlservices-class"></a>XamlServices 類別  
 您不一定需要處理 XAML 節點資料流。 如果您想要的基本載入路徑或儲存路徑的基本，您可以使用中的 Api<xref:System.Xaml.XamlServices>類別。  
  
-   各種不同的簽章的<xref:System.Xaml.XamlServices.Load%2A>實作載入路徑。 您可以載入檔案或資料流，或可以載入<xref:System.Xml.XmlReader>，<xref:System.IO.TextReader>或<xref:System.Xaml.XamlReader>，包裝您的 XAML 輸入，方法是使用該讀取器 Api 載入。  
  
-   各種不同的簽章<xref:System.Xaml.XamlServices.Save%2A>儲存的物件圖形，並產生輸出資料流、 檔案，或<xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter>執行個體。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> 將 XAML 轉換藉由連結的載入路徑和儲存路徑做為單一作業。 ，則可以使用不同的結構描述內容或不同的支援型別系統<xref:System.Xaml.XamlReader>和<xref:System.Xaml.XamlWriter>，這是影響產生的 XAML 轉換的方式。  
  
 如需有關如何使用<xref:System.Xaml.XamlServices>，請參閱 < [XAMLServices 類別和基本 XAML 讀取或寫入](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md)。  
  
## <a name="xaml-type-system"></a>XAML 類型系統  
 XAML 類型系統會提供與指定之個別節點的 XAML 節點資料流所需的 Api。  
  
 <xref:System.Xaml.XamlType> 您正在處理的開始物件節點與結束物件節點之間是一個物件的表示法。  
  
 <xref:System.Xaml.XamlMember> 您正在處理的開始成員節點與結束成員節點之間的情況下是成員的一個物件的表示法。  
  
 這類 Api<xref:System.Xaml.XamlType.GetAllMembers%2A>並<xref:System.Xaml.XamlType.GetMember%2A>並<xref:System.Xaml.XamlMember.DeclaringType%2A>報表之間的關聯性<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>。  
  
 .NET Framework XAML 服務實作的 XAML 類型系統的預設行為根據 common language runtime (CLR)、 和靜態分析的組件中的 CLR 類型使用反映。 因此，針對特定的 CLR 類型，XAML 類型系統的預設實作可以公開該類型和其成員的 XAML 結構描述，並報告方面的 XAML 類型系統。 在預設 XAML 類型系統中，類型的指派性的概念對應到 CLR 繼承，並執行個體、 實值型別等等的概念也會對應至支援的行為和 CLR 功能。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 語言功能的參考  
 若要支援 XAML，.NET Framework XAML 服務會提供為 XAML 語言 XAML 命名空間所定義的 XAML 語言概念的特定實作。 這些會記載為特定的參考頁面。 從 XAML 讀取器或.NET Framework XAML 服務所定義的 XAML 寫入器處理它們時，這些語言功能的行為方式的觀點來看記載的語言功能。 如需詳細資訊，請參閱 [XAML Namespace (x:) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。
