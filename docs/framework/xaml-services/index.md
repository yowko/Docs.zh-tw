---
title: XAML 服務
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 8e1e8dc9a1410d05c19e4dd1bccb30c65d7c5e66
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837281"
---
# <a name="xaml-services"></a>XAML 服務
本主題描述技術集的功能，稱為 .NET Framework XAML 服務。 所描述的大部分服務和 Api 都位於元件 system.string 中，這是以 .NET core 元件 .NET Framework 4 組引進的元件。 服務包括讀取器和寫入器、架構類別和架構支援、factory、類別的特性、XAML 語言內建支援，以及其他 XAML 語言功能。  
  
## <a name="about-this-documentation"></a>關於本檔  
 .NET Framework XAML 服務的概念檔假設您先前已具備 XAML 語言的經驗，以及如何將它套用至特定架構（例如 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 或 Windows Workflow Foundation）或特定的技術功能區域（例如 <xref:Microsoft.Build.Framework.XamlTypes>中的組建自訂功能）。 本檔不會嘗試以標記語言、XAML 語法術語或其他簡介材料來說明 XAML 的基本概念。 相反地，本檔著重于特別使用在 System.object 元件庫中啟用的 .NET Framework XAML 服務。 這些 Api 大多適用于 XAML 語言整合和擴充性的案例。 這可能包括下列任何一項：  
  
- 延伸基底 XAML 讀取器或 XAML 撰寫者的功能（直接處理 XAML 節點資料流程; 衍生您自己的 XAML 讀取器或 XAML 寫入器）。  
  
- 定義 XAML 可用的自訂型別，這些型別沒有特定的架構相依性，並將型別設為將 XAML 類型系統特性傳遞給 .NET Framework XAML 服務的類型。  
  
- 將 XAML 讀取器或 XAML 寫入器裝載為應用程式的元件，例如視覺化設計工具或 XAML 標記來源的互動式編輯器。  
  
- 撰寫 XAML 值轉換器（標記延伸; 自訂類型的類型轉換器）。  
  
- 定義自訂的 XAML 架構內容（使用支援類型來源的替代元件載入技術）; 使用已知型別查閱技術，而不是一律反映元件; 使用未使用 CLR `AppDomain` 和其相關聯安全性模型的載入元件概念。  
  
- 延伸基底 XAML 型別系統。  
  
- 使用 `Lookup` 或 `Invoker` 技術來影響 XAML 型別系統，以及如何評估型別 backings。  
  
 如果您是以語言尋找 XAML 的簡介材料，您可能會嘗試[Xaml 總覽（WPF）](../../desktop-wpf/fundamentals/xaml.md)。 該主題討論 XAML 的物件，這兩者都是 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 的，同時也使用 XAML 標記和 XAML 語言功能。 另一個有用的檔是[XAML 語言規格](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))中的簡介材料。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>在 .NET 架構中 .NET Framework XAML 服務和 .Xaml  
 在舊版的 Microsoft .NET Framework 中，XAML 語言功能的支援是由建基於 Microsoft .NET Framework （[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、Windows Workflow Foundation 和 Windows Communication Foundation （WCF））的架構所實，因此會根據您所使用的特定架構而有不同的行為和使用的 API。 這包括 XAML 剖析器及其物件圖形建立機制、XAML 語言內建函式、序列化支援等等。  
  
 在 .NET Framework 4 中，.NET Framework XAML 服務和 System.object 元件會定義支援 XAML 語言功能所需的大部分內容。 這包括 XAML 讀取器和 XAML 寫入器的基類。 新增至不在任何架構特定 XAML 執行中 .NET Framework XAML 服務的最重要功能，就是 XAML 的類型系統標記法。 型別系統表示以物件導向的方式呈現 XAML，而不需要依賴架構的特定功能。  
  
 XAML 類型系統不受限於 XAML 來源的標記表單或執行時間細節;也不會受到任何特定支援類型系統的限制。 XAML 類型系統包含類型、成員、XAML 架構內容、XML 層級概念，以及其他 XAML 語言概念或 XAML 內建函式的物件標記法。 使用或擴充 XAML 類型系統，可讓您從 XAML 讀取器和 XAML 寫入器之類的類別衍生，並將 XAML 標記法的功能延伸至架構、技術或使用或的應用程式所啟用的特定功能發出 XAML。 XAML 架構內容的概念可讓您從 XAML 物件寫入器實作為組合的實際物件圖形寫入作業，這是一種技術的支援類型系統，會透過內容中的元件資訊與 XAML 節點進行通訊來源. 如需 XAML 架構概念的詳細資訊。 請參閱[預設的 XAML 架構內容和 WPF XAML 架構內容](default-xaml-schema-context-and-wpf-xaml-schema-context.md)。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML 節點資料流程、XAML 讀取器和 XAML 撰寫者  
 若要瞭解 .NET Framework XAML 服務在 XAML 語言與使用 XAML 做為語言之特定技術之間的關聯性中所扮演的角色，請瞭解 XAML 節點資料流程的概念，以及該概念如何將 API 圖形與庫. XAML 節點資料流程是 xaml 語言標記法與 XAML 代表或定義的物件圖形之間的概念中繼。  
  
- XAML 讀取器是以某種形式處理 XAML，並產生 XAML 節點資料流程的實體。 在 API 中，XAML 讀取器是由基底類別 <xref:System.Xaml.XamlReader>來表示。  
  
- XAML 寫入器是處理 XAML 節點資料流程並產生其他內容的實體。 在 API 中，XAML 寫入器是由基底類別 <xref:System.Xaml.XamlWriter>來表示。  
  
 與 XAML 有關的兩個最常見案例是載入 XAML 來具現化物件圖形，並從應用程式或工具儲存物件圖形，並產生 XAML 標記法（通常會在標記表單中儲存為文字檔）。 在此檔中，載入 XAML 和建立物件圖形通常稱為載入路徑。 將現有的物件圖形儲存或序列化為 XAML 通常在此檔中稱為儲存路徑。  
  
 最常見的載入路徑類型可以描述如下：  
  
- 以 UTF 編碼的 XML 格式啟動 XAML 標記法，並儲存為文字檔。  
  
- 將該 XAML 載入 <xref:System.Xaml.XamlXmlReader>。 <xref:System.Xaml.XamlXmlReader> 是 <xref:System.Xaml.XamlReader> 子類別。  
  
- 結果是 XAML 節點資料流程。 您可以使用 <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API 來存取 XAML 節點資料流程的個別節點。 這裡最常見的作業是透過 XAML 節點資料流程，使用「目前的記錄」比喻來處理每個節點。  
  
- 將產生的節點從 XAML 節點資料流程傳遞至 <xref:System.Xaml.XamlObjectWriter> API。 <xref:System.Xaml.XamlObjectWriter> 是 <xref:System.Xaml.XamlWriter> 子類別。  
  
- <xref:System.Xaml.XamlObjectWriter> 會根據來源 XAML 節點資料流程的進度，一次寫入一個物件圖形（一個物件）。 這是透過 XAML 架構內容的協助，以及可以存取支援類型系統和架構之元件和類型的實作為來完成。  
  
- 呼叫 XAML 節點資料流程結尾的 <xref:System.Xaml.XamlObjectWriter.Result%2A>，以取得物件圖形的根物件。  
  
 最常見的儲存路徑類型可以描述如下：  
  
- 從整個應用程式執行時間的物件圖形、執行時間的 UI 內容和狀態，或在執行時間的整體應用程式物件表示的較社區段開始。  
  
- 從邏輯起始物件（例如應用程式根目錄或檔根目錄），將物件載入 <xref:System.Xaml.XamlObjectReader>。 <xref:System.Xaml.XamlObjectReader> 是 <xref:System.Xaml.XamlReader> 子類別。  
  
- 結果是 XAML 節點資料流程。 您可以使用 <xref:System.Xaml.XamlObjectReader> 和 <xref:System.Xaml.XamlReader> API 來存取 XAML 節點資料流程的個別節點。 這裡最常見的作業是透過 XAML 節點資料流程，使用「目前的記錄」比喻來處理每個節點。  
  
- 將產生的節點從 XAML 節點資料流程傳遞至 <xref:System.Xaml.XamlXmlWriter> API。 <xref:System.Xaml.XamlXmlWriter> 是 <xref:System.Xaml.XamlWriter> 子類別。  
  
- <xref:System.Xaml.XamlXmlWriter> 會以 XML UTF 編碼方式寫入 XAML。 您可以將它儲存為文字檔、資料流程或其他形式。  
  
- 呼叫 <xref:System.Xaml.XamlXmlWriter.Flush%2A> 以取得最終輸出。  
  
 如需 XAML 節點資料流程概念的詳細資訊，請參閱[瞭解 Xaml 節點資料流程結構和概念](understanding-xaml-node-stream-structures-and-concepts.md)。  
  
### <a name="the-xamlservices-class"></a>XamlServices 類別  
 不一定需要處理 XAML 節點資料流程。 如果您想要基本的載入路徑或基本儲存路徑，您可以使用 <xref:System.Xaml.XamlServices> 類別中的 Api。  
  
- 各種 <xref:System.Xaml.XamlServices.Load%2A> 的簽章會執行載入路徑。 您可以載入檔案或資料流程，也可以載入 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader> 或 <xref:System.Xaml.XamlReader>，藉由載入該讀取器的 Api 來包裝您的 XAML 輸入。  
  
- 各種不同的簽章 <xref:System.Xaml.XamlServices.Save%2A> 儲存物件圖形，並產生資料流程、檔案或 <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> 實例的輸出。  
  
- <xref:System.Xaml.XamlServices.Transform%2A> 藉由將載入路徑和儲存路徑連結為單一作業來轉換 XAML。 不同的架構內容或不同的支援類型系統可用於 <xref:System.Xaml.XamlReader> 和 <xref:System.Xaml.XamlWriter>，這會影響所產生之 XAML 的轉換方式。  
  
 如需如何使用 <xref:System.Xaml.XamlServices>的詳細資訊，請參閱[XAMLServices 類別和基本 XAML 讀取或寫入](xamlservices-class-and-basic-xaml-reading-or-writing.md)。  
  
## <a name="xaml-type-system"></a>XAML 類型系統  
 XAML 類型系統提供了使用 XAML 節點資料流程的特定個別節點所需的 Api。  
  
 <xref:System.Xaml.XamlType> 是物件的標記法-[開始物件] 節點和 [結束物件] 節點之間正在處理的內容。  
  
 <xref:System.Xaml.XamlMember> 是物件成員的標記法-您在 [啟動成員] 節點和 [結束成員] 節點之間的處理方式。  
  
 <xref:System.Xaml.XamlType.GetAllMembers%2A> 和 <xref:System.Xaml.XamlType.GetMember%2A> 和 <xref:System.Xaml.XamlMember.DeclaringType%2A> 之類的 Api 會報告 <xref:System.Xaml.XamlType> 與 <xref:System.Xaml.XamlMember>之間的關聯性。  
  
 .NET Framework XAML 服務所實作為之 XAML 類型系統的預設行為是以 common language runtime （CLR）為基礎，並使用反映在元件中進行 CLR 類型的靜態分析。 因此，針對特定 CLR 類型，XAML 類型系統的預設實值可以公開該類型及其成員的 XAML 架構，並根據 XAML 類型系統來進行報告。 在預設的 XAML 類型系統中，xaml 類型的概念會對應到 CLR 繼承，而實例、實數值型別等的概念也會對應至 CLR 的支援行為和功能。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 語言功能的參考  
 為了支援 XAML，.NET Framework XAML 服務會提供 xaml 語言概念的特定執行，如 XAML 語言 XAML 命名空間所定義。 這些會記錄為特定的參考頁面。 當語言功能是由 XAML 讀取器或 .NET Framework XAML 服務所定義的 XAML 寫入器進行處理時，會從這些語言功能的行為角度來記載。 如需詳細資訊，請參閱 [XAML Namespace (x:) Language Features](xaml-namespace-x-language-features.md)。
