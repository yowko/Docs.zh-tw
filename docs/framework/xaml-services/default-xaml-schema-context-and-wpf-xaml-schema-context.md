---
title: "預設 XAML 結構描述內容和 WPF XAML 結構描述內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ee7c83868934f1a524bb0068ea5e749e6cbfab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>預設 XAML 結構描述內容和 WPF XAML 結構描述內容
XAML 結構描述內容是概念性的實體，會限定使用特定的 XAML 詞彙的 XAML 生產環境與撰寫的行為，包含型別對應的解析，載入組件的方式、 如何特定讀取器和寫入器物件之間的互動方式設定會被解譯。 本主題描述.NET Framework XAML 服務和相關聯的預設 XAML 結構描述內容，以 CLR 型別系統為基礎的功能。 本主題也描述適用於 WPF XAML 結構描述內容。  
  
## <a name="default-xaml-schema-context"></a>預設 XAML 結構描述內容  
 .NET framework XAML 服務實作並使用預設 XAML 結構描述內容。 預設 XAML 結構描述內容行為不一定完全可見的 API 中<xref:System.Xaml.XamlSchemaContext>類別。 不過，在許多情況下會影響預設 XAML 結構描述內容的行為是透過通用 API 的 XAML 類型系統，例如的成員可觀察<xref:System.Xaml.XamlMember>或<xref:System.Xaml.XamlType>，或透過公開在 XAML 讀取器和 XAML 寫入器所使用的應用程式開發介面預設 XAML 結構描述內容。  
  
 您可以建立<xref:System.Xaml.XamlSchemaContext>藉由呼叫封裝的預設行為<xref:System.Xaml.XamlSchemaContext>建構函式。 此明確建立的預設 XAML 結構描述內容。 如果您的 XAML 讀取器或 XAML 寫入器使用 Api 時，不會明確地初始化隱含地建立相同的預設 XAML 結構描述內容<xref:System.Xaml.XamlSchemaContext>輸入的參數。  
  
 預設 XAML 結構描述內容依賴 CLR 反映型別對應的行為。 這包括檢查定義 CLR <xref:System.Type>，與相關<xref:System.Reflection.PropertyInfo>或<xref:System.Reflection.MethodInfo>。 此外，型別或成員上的 CLR 屬性使用以便填滿的細節，以利 XAML 型別或使用 CLR 支援類型的 XAML 成員資訊。 預設 XAML 結構描述內容不需要型別系統延伸技術，例如`Invoker`模式，因為使用的 CLR 型別系統所需的資訊。  
  
 針對組件載入的邏輯的預設 XAML 結構描述內容依賴主要是根據 XAML 命名空間對應中提供的任何組件值。 此外，<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>可以提示載入，案例，例如載入內部類型的組件。  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML 結構描述內容  
 本主題中說明的 WPF XAML 結構描述內容，因為的 WPF 實作提供有趣的功能，可以藉由實作非預設 XAML 結構描述內容中導入之類型的說明。 此外，XAML 結構描述內容概念並不討論關於太大，WPF XAML; WPF 文件中啟用 XAML 結構描述內容的行為可能只會完全可了解如果的預設 XAML 結構描述內容的運作方式的討論與整合。 WPF XAML 結構描述內容會實作下列的行為。  
  
 **查閱會覆寫：** WPF xaml 中有少數的內容模型中所沒有的函式的 XAML 內容屬性<xref:System.Windows.Markup.ContentPropertyAttribute>屬性化。 <xref:System.Xaml.XamlType.LookupContentProperty%2A>覆寫的 WPF 實作這種行為。  
  
 **WPF 運算式的延遲：** WPF 功能延後的值，直到執行階段內容可供使用的數個運算式類別。 此外，範本擴充是依賴延遲技術的執行階段行為。  
  
 **輸入系統查閱最佳化：** WPF 必須廣泛 XAML 詞彙和物件模型，其中包含數百個 WPF 定義類別繼承的基底類別成員定義。 此外，WPF 本身橫跨數個組件。 WPF 可最佳化使用查閱資料表和其他技術其型別查閱。 這提供效能改良的預設 XAML 結構描述內容和其 CLR 型別查閱。 在其中型別不在查閱資料表的情況下，行為會使用類似於預設 XAML 結構描述內容的 XAML 結構描述內容技巧。  
  
 **XamlType 和 XamlMember 副檔名：** WPF 擴充屬性具有相依性屬性的概念和事件概念與路由事件。 若要提供更好的可見度這些概念的 XAML 處理作業，WPF 擴充<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>，並將報告相依性屬性和路由傳送事件特性的內部屬性。  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>存取 WPF XAML 結構描述內容  
 如果您使用 XAML 技術為基礎之 WPF 的<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>或<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>，WPF XAML 結構描述內容已在使用這些 XAML 讀取器和 XAML 寫入器實作。  
  
 如果您使用其他 XAML 讀取器或未初始化的 XAML 寫入器實作與 WPF XAML 結構描述內容，您可以取得可運作的 WPF XAML 結構描述內容從<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>。 您接著可以使用此值為使用其他 API 的初始化<xref:System.Xaml.XamlSchemaContext>。 例如，您可以呼叫<xref:System.Xaml.XamlXmlReader.%23ctor%2A>初始化和傳遞 WPF XAML 結構描述內容。 或者，您可以使用 WPF XAML 結構描述內容，XAML 類型系統作業。 這可能包括建構初始化<xref:System.Xaml.XamlType>或<xref:System.Xaml.XamlMember>，或呼叫<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>。  
  
 請注意，是否您從純 XAML 節點資料流角度存取 WPF XAML 的某些方面，WPF 架構功能可能未動作尚未。 例如，WPF 控制項的範本不尚未套用。 因此如果您存取此屬性，在執行階段可能會填入完整的視覺化樹狀結構時，您可能只會看到參考範本的屬性值。 WPF 標記延伸提供的服務內容也可能不正確所提供的非執行階段的情況下，如果，可能會導致例外狀況時，嘗試寫入物件圖形。  
  
## <a name="xaml-and-assembly-loading"></a>XAML 和組件載入  
 組件載入的 XAML 和.NET Framework XAML 服務整合的 CLR 定義概念<xref:System.AppDomain>。 XAML 結構描述內容將解釋如何載入組件或尋找在執行的階段或設計階段類型，根據使用<xref:System.AppDomain>和其他因素而定。 邏輯是根據 XAML 是鬆散的 XAML，XAML 讀取器稍有不同，是編譯成 DLL 的 XAML `XamlBuildTask`，或 BAML 產生 WPF 的`PresentationBuildTask`。  
  
 WPF 應用程式模型，接著會採用與整合，WPF 的 XAML 結構描述內容<xref:System.AppDomain>以及其他因素的 WPF 實作詳細資料。  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML 讀取器輸入 (鬆散的 XAML)  
  
1.  XAML 結構描述內容逐一<xref:System.AppDomain>應用程式中，尋找符合名稱的所有層面的已載入組件的最近從最開始載入的組件。 如果找到相符項目，該組件用於解析。  
  
2.  否則，下列技術的其中一個基礎 CLR <xref:System.Reflection.Assembly> API 可用來載入組件：  
  
    -   如果名稱限定在對應中，呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>上的限定名稱。  
  
    -   如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
    -   如果名稱是在對應中不合格，呼叫<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>。  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask`用於[!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]和[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]。  
  
 請注意，組件參考透過`XamlBuildTask`一定是完整格式。  
  
1.  呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>上的限定名稱。  
  
2.  如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 有 BAML 的組件載入至兩個層面： 載入初始的組件，其中包含做為元件，BAML 及載入 BAML 生產所參考的任何類型的型別支援組件。  
  
##### <a name="assembly-load-for-initial-markup"></a>組件載入初始的標記：  
 一律會不合格載入標記的來源組件的參考。  
  
1.  WPF XAML 結構描述內容逐一<xref:System.AppDomain>WPF 應用程式中，尋找符合名稱的所有層面的已載入組件的最近從最開始載入的組件。 如果找到相符項目，該組件用於解析。  
  
2.  如果上一個步驟失敗時，使用簡短名稱 （和公開金鑰語彙基元如果有的話） 來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
##### <a name="assembly-references-by-baml-types"></a>BAML 類型的組件參考：  
 在 BAML 生產環境中使用類型的組件參考一律會完整名稱，做為建置工作的輸出。  
  
1.  WPF XAML 結構描述內容逐一<xref:System.AppDomain>WPF 應用程式中，尋找符合名稱的所有層面的已載入組件的最近從最開始載入的組件。 如果找到相符項目，該組件用於解析。  
  
2.  否則，載入組件會使用其中一個的下列技術：  
  
    -   呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>上的限定名稱。  
  
    -   如果簡短名稱 + 公開金鑰語彙基元組合 BAML 已從載入的組件中，使用該組件。  
  
    -   使用簡短名稱 + 公開金鑰語彙基元來呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>請參閱  
 [認識 XAML 節點資料流結構和概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
