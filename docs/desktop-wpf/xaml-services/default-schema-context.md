---
title: 預設 XAML 結構描述內容和 WPF XAML 結構描述內容
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071861"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>預設 XAML 結構描述內容和 WPF XAML 結構描述內容
XAML 架構上下文是一個概念實體,它限定了使用特定 XAML 詞彙表的 XAML 生產如何與物件寫入行為進行交互,包括類型映射解析方式、程式集的載入方式、如何解釋某些讀取器和編寫器設置。 本主題介紹 .NET XAML 服務的功能和基於 CLR 類型系統的關聯的預設 XAML 架構上下文。 本主題還介紹用於 WPF 的 XAML 架構上下文。

## <a name="default-xaml-schema-context"></a>預設 XAML 架構內容

.NET XAML 服務既實現並使用預設的 XAML 架構上下文。 預設 XAML 架構上下文行為並不<xref:System.Xaml.XamlSchemaContext>總是在 類的 API 中完全可見。 但是,在許多情況下,預設 XAML 架構上下文影響的行為可以透過 XAML 類型系統的<xref:System.Xaml.XamlMember>常見 API(如或的成員<xref:System.Xaml.XamlType>或 或透過使用預設 XAML 架構上下文的 XAML 讀取器和 XAML 寫入器上公開的 API 來觀察)。

可以透過呼叫式函數<xref:System.Xaml.XamlSchemaContext>建立封裝預設行為<xref:System.Xaml.XamlSchemaContext>的 。 這顯式創建預設的 XAML 架構上下文。 如果使用不顯式採用<xref:System.Xaml.XamlSchemaContext>輸入參數的 API 初始化 XAML 讀取器或 XAML 編寫器,則隱式創建相同的預設 XAML 架構上下文。

預設 XAML 架構上下文依賴於 CLR 反射的類型映射行為。 這包括檢查定義的 CLR<xref:System.Type><xref:System.Reflection.PropertyInfo>和<xref:System.Reflection.MethodInfo>相關 或 。 此外,使用類型或成員的 CLR 歸因來填寫使用 CLR 支援類型的 XAML 類型或 XAML 成員資訊的詳細資訊。 預設 XAML 架構上下文不需要類型系統擴展技術`Invoker`(如模式),因為 CLR 類型系統提供了必要的資訊。

對於程式集載入邏輯,預設 XAML 架構上下文主要依賴於 XAML 命名空間映射中提供的任何程式集值。 此外,<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>還可以提示要載入的程式集,用於載入內部類型等方案。

## <a name="wpf-xaml-schema-context"></a>WPF XAML 架構內容

本主題將介紹 WPF XAML 架構上下文,因為 WPF 實現提供了通過實現非預設 XAML 架構上下文可以引入的功能類型的有趣說明。 此外,解決 WPF XAML 的 WPF 文檔中沒有過多討論 XAML 架構上下文概念;僅當與討論預設 XAML 架構上下文的工作原理集成時,XAML 架構上下文啟用的行為可能完全可以理解。 WPF XAML 架構上下文實現以下行為。

**尋找覆寫:** WPF 具有一些適用於 XAML 的內容模型,其中有<xref:System.Windows.Markup.ContentPropertyAttribute>XAML 內容 屬性,這些屬性在不被歸因的情況下起作用。 <xref:System.Xaml.XamlType.LookupContentProperty%2A>覆蓋 WPF 實現此行為。

**WPF 表示式的延遲:** WPF 具有多個運算式類,這些運算式類將值延遲到運行時上下文可用。 此外,範本擴展是依賴於延遲技術的運行時行為。

**類型系統搜尋最佳化:** WPF 具有廣泛的 XAML 詞彙表和物件模型,包括繼承到數百個 WPF 定義的類的基類成員定義。 此外,WPF 本身分佈在多個程式集中。 WPF 使用查找表和其他技術優化其類型查找。 這提供了與預設 XAML 架構上下文及其基於 CLR 的類型查找的性能改進。 在查找表中不存在類型的情況下,行為使用類似於預設 XAML 架構上下文的 XAML 架構上下文技術。

**XamlType 和 Xaml 成員延伸:** WPF 擴展具有依賴項屬性的屬性概念,以及具有路由事件的事件概念。 為了給這些概念提供 XAML 處理操作的更大可見性,WPF<xref:System.Xaml.XamlType><xref:System.Xaml.XamlMember>擴展和,並添加報告依賴項屬性和路由事件特徵的內部屬性。

### <a name="accessing-the-wpf-xaml-schema-context"></a>存取 WPF XAML 架構內容

如果您使用的是基於<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>WPF<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>或的 XAML 技術,則 WPF XAML 架構上下文已在這些 XAML 讀取器和 XAML 編寫器實現上使用。

如果使用其他未使用 WPF XAML 架構上下文初始化的 XAML 讀取器或 XAML 編<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>寫器實現,則可以從 獲取工作 WPF XAML 架構上下文。 然後,可以將此值用作使用的其他 API 的<xref:System.Xaml.XamlSchemaContext>初始化 。 例如,您可以調用<xref:System.Xaml.XamlXmlReader.%23ctor%2A>初始化並傳遞 WPF XAML 架構上下文。 或者,您可以將 WPF XAML 架構上下文用於 XAML 類型系統操作。 這可能包含<xref:System.Xaml.XamlType>或<xref:System.Xaml.XamlMember>的建構初始化或呼叫<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>。

請注意,如果從純 XAML 節點流的角度來看訪問 WPF XAML 的某些方面,則某些 WPF 框架功能可能尚未執行。 例如,尚未應用控制件的 WPF 範本。 因此,如果您訪問在運行時可能使用完整可視化樹填充的屬性,則可能只看到引用範本的屬性值。 如果從非運行時情況提供,則為 WPF 標記擴展提供的服務上下文也可能不準確,並且在嘗試寫入物件圖時可能會導致異常。

## <a name="xaml-and-assembly-loading"></a>XAML 和裝配載

XAML 和 .NET XAML 服務的程式集載入與CLR定義的概<xref:System.AppDomain>念整合在一起。 XAML 架構上下文根據<xref:System.AppDomain>使用 和其他因素解釋如何在運行時或設計時載入程式集或查找類型。 邏輯略有不同,具體取決於 XAML 對於 XAML 讀取器是鬆散的 XAML,XAML 是否由`XamlBuildTask`編譯為 DLL,還是由 WPF 生成的`PresentationBuildTask`BAML。

WPF 的 XAML 架構上下文與 WPF<xref:System.AppDomain>應用程式模型整合,而 WPF 應用程式模型又使用 WPF 實現詳細資訊的其他因素。

#### <a name="xaml-reader-input-loose-xaml"></a>XAML讀卡機輸入(鬆散 XAML)

01. XAML 架構上下文遍<xref:System.AppDomain>達 應用程式,查找與名稱的所有方面匹配的已載入程式集,從最近載入的程式集開始。 如果找到匹配項,則該程式集用於解析。

02. 否則,基於 CLR <xref:System.Reflection.Assembly> API 的以下技術之一用於載入程式集:

    - 如果名稱在映射中限定,則調用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>限定名稱。

    - 如果上一步驟失敗,請使用短名稱(如果存在公開金鑰) 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。

    - 如果名稱在映射中為非限定,請<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>呼叫 。

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`用於 Windows 通信基礎 (WCF) 和 Windows 工作流基礎。

請注意,通過的`XamlBuildTask`程式集引用始終完全限定。

1. 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名。

2. 如果上一步驟失敗,請使用短名稱(如果存在公開金鑰) 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。

#### <a name="baml-presentationbuildtask"></a>BAML (示範編譯工作)

BAML 的程式集載入有兩個方面:載入包含 BAML 作為元件的初始程式集,以及為 BAML 生產引用的任何類型的類型載入類型支援程式集。

##### <a name="assembly-load-for-initial-markup"></a>初始標記的載入負載:

對程式集的引用始終不限定以載入標記。

1. WPF XAML 架構上下文遍達 WPF<xref:System.AppDomain>應用程式的, 尋找與名稱的所有方面符合的已載入程式集,從最近載入的程式集開始。 如果找到匹配項,則該程式集用於解析。

2. 如果上一步驟失敗,請使用短名稱(如果存在公開金鑰) 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>。

##### <a name="assembly-references-by-baml-types"></a>依 BAML 類型進行的程式集引用:

作為生成任務的輸出,BAML 生產中使用的類型的程式集引用始終完全限定。

01. WPF XAML 架構上下文遍達 WPF<xref:System.AppDomain>應用程式的, 尋找與名稱的所有方面符合的已載入程式集,從最近載入的程式集開始。 如果找到匹配項,則該程式集用於解析。

02. 否則,使用以下技術之一載入程式集:

    - 呼叫<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名。
  
    - 如果短名稱 + 公開金鑰與從 BAML 載入的程式集匹配,請使用該程式集。

    - 使用短名稱 + 公開金<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>鑰的權碼呼叫 。

## <a name="see-also"></a>另請參閱

- [認識 XAML 節點資料流結構和概念](understanding-xaml-node-stream-structures-and-concepts.md)
