---
title: 預設 XAML 結構描述內容和 WPF XAML 結構描述內容
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 0d6a0aa80d8490c509fa9036f88d4f6863ff040c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295597"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>預設 XAML 結構描述內容和 WPF XAML 結構描述內容
XAML 結構描述內容是限定使用特定的 XAML 詞彙的 XAML 生產環境與撰寫行為，包括類型對應的解析，已載入組件的方式、 如何特定讀取器和寫入器物件之間的互動方式在概念實體設定會被解譯。 本主題描述.NET Framework XAML 服務和相關聯的預設 XAML 結構描述內容，以 CLR 型別系統為基礎的功能。 本主題也描述用於 WPF 的 XAML 結構描述內容。  
  
## <a name="default-xaml-schema-context"></a>預設 XAML 結構描述內容  
 .NET framework XAML 服務同時實作，並使用預設 XAML 結構描述內容。 預設 XAML 結構描述內容行為不一定在 API 中完整可見<xref:System.Xaml.XamlSchemaContext>類別。 不過，在許多情況下會影響預設 XAML 結構描述內容的行為是透過通用 API 的 XAML 類型系統，例如的成員可預見值<xref:System.Xaml.XamlMember>或<xref:System.Xaml.XamlType>，或透過公開在 XAML 讀取器和 XAML 寫入器所使用的 Api預設 XAML 結構描述內容。  
  
 您可以建立<xref:System.Xaml.XamlSchemaContext>藉由呼叫封裝的預設行為<xref:System.Xaml.XamlSchemaContext>建構函式。 明確，這會建立預設 XAML 結構描述內容。 如果您初始化 XAML 讀取器或 XAML 寫入器使用 Api，明確地不會隱含地建立相同的預設 XAML 結構描述內容<xref:System.Xaml.XamlSchemaContext>輸入的參數。  
  
 預設 XAML 結構描述內容會依賴 CLR 反映其型別對應行為。 這包括檢查定義的 CLR <xref:System.Type>，與相關<xref:System.Reflection.PropertyInfo>或<xref:System.Reflection.MethodInfo>。 此外，類型或成員的 CLR 屬性用來填入 XAML 型別或使用 CLR 支援類型的 XAML 成員資訊的細節。 預設 XAML 結構描述內容不需要型別系統擴充技術，例如`Invoker`模式，因為使用 CLR 型別系統所需的資訊。  
  
 載入邏輯的組件，預設 XAML 結構描述內容主要是會依賴任何組件所提供值的 XAML 命名空間對應。 此外，<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>可以提示的組件載入，案例，例如載入內部型別。  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML 結構描述內容  
 本主題中說明 WPF XAML 結構描述內容，因為 WPF 實作提供有趣的功能可能會造成實作非預設 XAML 結構描述內容類型說明。 此外，XAML 結構描述內容的概念中不會討論非常位址 WPF XAML; 的 WPF 文件可讓 XAML 結構描述內容的行為可能只會完全了解如果與預設 XAML 結構描述內容的運作方式的討論區整合。 WPF XAML 結構描述內容會實作下列行為。  
  
 **查閱會覆寫：** WPF 的 XAML 中有少數的內容模型有 XAML 內容屬性，而函式<xref:System.Windows.Markup.ContentPropertyAttribute>屬性化。 <xref:System.Xaml.XamlType.LookupContentProperty%2A> 覆寫的 WPF 實作此行為。  
  
 **WPF 運算式的延遲：** WPF 提供數個延遲值，直到執行階段內容可供使用的運算式類別。 此外，範本展開是依賴延遲技術的執行階段行為。  
  
 **輸入系統查閱最佳化：** WPF 會有的廣泛 XAML 詞彙和物件模型，包括繼承至數百個 WPF 定義類別的基底類別成員定義。 此外，WPF 本身橫跨數個組件。 WPF 可最佳化使用查閱資料表和其他技術其型別查閱。 這是透過預設 XAML 結構描述內容和其 CLR 型別查閱可提升效能。 在其中型別不存在的查閱資料表的情況下，行為會使用 XAML 結構描述內容技巧，類似於預設 XAML 結構描述內容。  
  
 **XamlType 和 XamlMember 延伸模組：** 使用相依性屬性的屬性概念及使用路由事件的事件概念來擴充 WPF。 若要讓這些概念更高的可見性的 XAML 處理作業中，WPF 來擴充<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>，而且會加入內部屬性，報告相依性屬性和路由事件的特性。  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>存取 WPF XAML 結構描述內容  
 如果您使用以 WPF 為基礎的 XAML 技巧<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>或<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>，WPF XAML 結構描述內容已在使用這些 XAML 讀取器和 XAML 寫入器實作。  
  
 如果您使用其他 XAML 讀取器或未初始化的 XAML 寫入器實作與 WPF XAML 結構描述內容，您可以取得運作中的 WPF XAML 結構描述內容從<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>。 您接著可以使用此值為使用其他 api 的初始化<xref:System.Xaml.XamlSchemaContext>。 例如，您可以呼叫<xref:System.Xaml.XamlXmlReader.%23ctor%2A>輸入初始化，傳遞 WPF XAML 結構描述內容。 或者，您可以使用 WPF XAML 結構描述內容，XAML 類型系統作業。 這可能包括建構初始化<xref:System.Xaml.XamlType>或是<xref:System.Xaml.XamlMember>，或呼叫<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>。  
  
 請注意，是否您從單純的 XAML 節點資料流檢視方塊存取 WPF XAML 的某些層面，WPF framework 功能的一些可能不具有處理尚未。 比方說，WPF 控制項的範本是尚未套用。 因此如果您存取此屬性，在執行階段可能會填入完整視覺化樹狀結構時，您可能只會看到參考範本的屬性值。 所提供的 WPF 標記延伸的服務內容也可能不正確，如果提供非執行階段的情況下，並嘗試將寫入物件圖形時，會導致例外狀況。  
  
## <a name="xaml-and-assembly-loading"></a>XAML 和組件載入  
 組件載入的 XAML 和.NET Framework XAML 服務整合的 CLR 定義概念<xref:System.AppDomain>。 XAML 結構描述內容將解釋如何載入組件，或尋找型別在執行的階段或設計階段，根據使用<xref:System.AppDomain>以及其他因素。 邏輯是根據 XAML 是鬆散的 XAML，XAML 讀取器稍有不同，XAML 編譯成 DLL 所`XamlBuildTask`，或由 WPF 的產生 BAML `PresentationBuildTask`。  
  
 WPF 的 XAML 結構描述內容整合了 WPF 應用程式模型，它會使用<xref:System.AppDomain>以及其他因素，是 WPF 實作詳細資料。  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML 讀取器輸入 (鬆散的 XAML)  
  
1. 逐一查看 XAML 結構描述內容<xref:System.AppDomain>的應用程式中，尋找符合名稱的所有層面的已載入組件從最開始的最近載入的組件。 如果找到相符項目，則該組件用於解析。  
  
2. 下列技術之一，否則為根據 CLR <xref:System.Reflection.Assembly> API 用來載入組件：  
  
    -   如果為限定名稱，在對應中，呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名稱。  
  
    -   如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
    -   如果在對應中的非限定名稱，呼叫<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>。  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` 使用於 Windows Communication Foundation (WCF) 和 Windows Workflow Foundation。  
  
 請注意，組件參考透過`XamlBuildTask`一律是完整限定。  
  
1. 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名稱。  
  
2. 如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 有兩個層面需要組件載入為 BAML： 載入初始的組件，其中包含做為元件，BAML 和載入型別支援的組件的 BAML 生產所參考的任何型別。  
  
##### <a name="assembly-load-for-initial-markup"></a>初始標記的組件載入：  
 若要載入標記的來源組件的參考總是不合格。  
  
1. WPF XAML 結構描述內容逐一<xref:System.AppDomain>的 WPF 應用程式中，尋找符合名稱的所有層面的已載入組件從最開始的最近載入的組件。 如果找到相符項目，則該組件用於解析。  
  
2. 如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
##### <a name="assembly-references-by-baml-types"></a>BAML 類型的組件參考：  
 BAML 生產環境中所使用之類型的組件參考一律是完整名稱，作為建置工作的輸出。  
  
1. WPF XAML 結構描述內容逐一<xref:System.AppDomain>的 WPF 應用程式中，尋找符合名稱的所有層面的已載入組件從最開始的最近載入的組件。 如果找到相符項目，則該組件用於解析。  
  
2. 否則，下列技術的其中一個用來載入組件：  
  
    -   呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名稱。  
  
    -   如果簡短名稱 + 公開金鑰語彙基元組合符合 BAML 從載入的組件中，使用該組件。  
  
    -   使用簡短名稱 + 公開金鑰語彙基元來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱

- [認識 XAML 節點資料流結構和概念](understanding-xaml-node-stream-structures-and-concepts.md)
