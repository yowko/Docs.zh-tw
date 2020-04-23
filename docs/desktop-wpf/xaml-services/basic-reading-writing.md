---
title: XAMLServices 類別和基本 XAML 的讀取或寫入
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071875"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAML服務類別和基本的XAML閱讀或寫作

<xref:System.Xaml.XamlServices>是 .NET 提供的類,可用於解決不需要特定存取 XAML 節點流或從這些節點獲取的 XAML 類型系統資訊的 XAML 方案。 <xref:System.Xaml.XamlServices>API 可以概括`Load`如下`Parse`:或支援 XAML`Save`載入路徑, 以支援 XAML 儲存路徑,並提供`Transform`連接載入路徑和儲存路徑的技術。 `Transform` 可從某個 XAML 結構描述變更為另一個 XAML 結構描述。 本主題摘要說明這些 API 分類，並說明特定方法多載之間的差異。

## <a name="load"></a>載入

<xref:System.Xaml.XamlServices.Load%2A> 有多種多載會實作載入路徑的完整邏輯。 載入路徑使用某種形式的 XAML，然後輸出 XAML 節點資料流。 這些載入路徑大多數會使用編碼 XML 文字檔形式的 XAML。 不過，您也可以載入一般資料流，或是載入已包含在其他 <xref:System.Xaml.XamlReader> 實作中的預先載入 XAML 來源。

就大部分的情節而言，最簡單的多載是 <xref:System.Xaml.XamlServices.Load%28System.String%29>。 這個多載具有 `fileName` 參數，也就是包含要載入之 XAML 的文字檔名稱。 這適用於先前已將狀態或資料序列化至本機電腦上的應用程式情節 (例如完全信任應用程式)。 也適用於您正在定義應用程式模型，並想要載入其中一個標準檔案的架構 (這個標準檔案會定義應用程式行為、起始 UI，或其他由架構定義並使用 XAML 的功能)。

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> 具有類似的情節。 如果您要讓使用者選擇要載入的檔案，則這個多載可能會很有用，因為 <xref:System.IO.Stream> 經常是其他可存取檔案系統的 <xref:System.IO> API 的輸出。 或者，您也可以透過非同步下載或其他同樣能夠提供資料流的網路技術，來存取 XAML 來源。 (從資料流或使用者選取的來源載入可能會有安全性隱憂。 如需詳細資訊，請參閱 [XAML Security Considerations](security-considerations.md)。)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>是<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>依賴於早期版本的 .NET 格式讀取器的重載。 要使用這些重載,您應該已經創建了一個讀取器實例,並使用其`Create`API 以相關形式(文本或 XML)載入 XAML。 如果您已移動其他讀取器中的記錄指標，或使用這些讀取器執行其他作業，則不重要。 <xref:System.Xaml.XamlServices.Load%2A> 中的載入路徑邏輯一律會從根目錄往下處理整個 XAML 輸入。 以下方案可能值得使用這些重載:

- 設計可讓您從現有的 XML 特定文字編輯器，提供簡單 XAML 編輯功能的介面。

- 核心 <xref:System.IO> 的衍生情節，此時您會使用專用讀取器來開啟檔案或資料流。 您的邏輯在嘗試將內容載入為 XAML 之前，會先對其執行初步的檢查或處理。

您可以載入檔案或流,也可以載入<xref:System.Xml.XmlReader><xref:System.IO.TextReader>、<xref:System.Xaml.XamlReader>或 透過載入讀取器的 API 來包裝 XAML 輸入。

就內部而言，上述每種多載最終都會是 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>，而其中傳遞的 <xref:System.Xml.XmlReader> 可用來建立新的 <xref:System.Xaml.XamlXmlReader>。

更進階情節適用的 `Load` 簽章是 <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>。 這個簽章可用於下列其中一種情況：

- 您已經定義了自己的實<xref:System.Xaml.XamlReader>作 。

- 您需要指定不同於預設值的 <xref:System.Xaml.XamlReader> 設定。

非預設設定的範例:

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

<xref:System.Xaml.XamlServices> 的預設讀取器為 <xref:System.Xaml.XamlXmlReader>。 如果提供自己的<xref:System.Xaml.XamlXmlReader>設定,則以下是設定為非<xref:System.Xaml.XamlXmlReaderSettings>預設 屬性:

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>剖析

<xref:System.Xaml.XamlServices.Parse%2A> 類似 `Load` ，因為它是一個會從 XAML 輸入建立 XAML 節點資料流的載入路徑 API。 不過，在本例中，XAML 輸入會直接以字串的形式提供，其中包含要載入的所有 XAML。 <xref:System.Xaml.XamlServices.Parse%2A> 是較適用於應用程式情節的輕量型方法，對架構情節而言較不適用。 如需詳細資訊，請參閱 <xref:System.Xaml.XamlServices.Parse%2A>。 <xref:System.Xaml.XamlServices.Parse%2A>只是一個涉及<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>內部的<xref:System.IO.StringReader>包接調用。

## <a name="save"></a>儲存

<xref:System.Xaml.XamlServices.Save%2A>實現存儲路徑的各種過載。 所有 <xref:System.Xaml.XamlServices.Save%2A> 方法都會接受物件圖形做為輸入，然後產生資料流、檔案或 <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> 執行個體等形式的輸出。

輸入物件必須是某個物件表示的根物件。 這可以是商務物件的單一根物件、UI 情節中頁面之物件樹狀目錄的根目錄、設計工具中的工作編輯介面，或是其他適用於情節的根物件概念。

在許多情況下,您保存的物件樹與載入 XAML 的原始操作相關,該操作與框架/<xref:System.Xaml.XamlServices.Load%2A>應用程式模型 實現的其他 API 一起載入或載入 XAML。 物件樹狀目錄中可能會出現差異，其原因包括狀態變更、應用程式擷取到使用者在執行階段做出的設定變更、由於應用程式是 XAML 設計介面而影響的 XAML 變更等等。無論是否有所變更，從標記載入 XAML 再儲存 XAML，然後比較兩個 XAML 標記格式的這個概念，有時會被視為 XAML 的反覆存取表示。

儲存和序列化以標記形式設定之複雜物件的挑戰，在於如何能夠完整表示而不遺漏資訊，同時又不致過於繁瑣而使 XAML 不易閱讀。 再者，不同的 XAML 客戶對於如何拿捏此一平衡，也有不同的定義或期望。 <xref:System.Xaml.XamlServices.Save%2A> API 就是該平衡的其中一種定義。 <xref:System.Xaml.XamlServices.Save%2A> API 使用可用的 XAML 結構描述內容，以及 <xref:System.Xaml.XamlType>、 <xref:System.Xaml.XamlMember>和其他 XAML 內建和 XAML 類型系統概念的預設 CLR 特性，來判斷特定 XAML 節點資料流建構在重新儲存成標記時可進行最佳化的位置。 例如， <xref:System.Xaml.XamlServices> 儲存路徑可使用以 CLR 為基礎的預設 XAML 結構描述內容，來解析物件的 <xref:System.Xaml.XamlType> 可判斷 <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>；接著可在將屬性寫入物件的 XAML 內容時，省略屬性項目標記。

<a name="transform"></a>
## <a name="transform"></a>轉換

<xref:System.Xaml.XamlServices.Transform%2A> 會藉由將載入路徑和儲存路徑連結成單一作業，來轉換 XAML。 <xref:System.Xaml.XamlReader> 和 <xref:System.Xaml.XamlWriter>則可能會使用不同的結構描述內容或支援類型系統，而影響產生之 XAML 的轉換方式。 這適用於各種轉換作業。

如果作業需要檢查 XAML 節點資料流中的每個節點，您通常不會使用 <xref:System.Xaml.XamlServices.Transform%2A>。 相反地，您需要定義自己的載入路徑-儲存路徑作業序列，並插入自己的邏輯。 請在其中一個路徑中，在您自己的節點迴圈周圍使用 XAML 讀取器/XAML 寫入器配對。 例如，使用 <xref:System.Xaml.XamlXmlReader> 載入初始 XAML，再以後續的 <xref:System.Xaml.XamlXmlReader.Read%2A> 呼叫逐步執行至各節點。 在 XAML 節點資料流層級上運作時，您現在可以調整個別節點 (類型、成員、其他節點) 以套用轉換，或讓節點保持原狀。 接著，您可以將節點繼續傳送至 `Write` 的相關 <xref:System.Xaml.XamlObjectWriter> API 並寫出物件。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML 服務](../../../api/index.md)
