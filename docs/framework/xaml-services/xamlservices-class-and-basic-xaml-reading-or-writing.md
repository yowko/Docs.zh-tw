---
title: XAMLServices 類別和基本 XAML 的讀取或寫入
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 27c7a45a45e8bbe3594813b29344d1548eecda5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>XAMLServices 類別和基本 XAML 的讀取或寫入
<xref:System.Xaml.XamlServices> 是 .NET Framework XAML 服務所提供的類別，可用來解決不需要特別存取 XAML 節點資料流，或取自這些節點之 XAML 類型系統資訊的 XAML 情節。 <xref:System.Xaml.XamlServices> API 可摘述如下： `Load` 或 `Parse` 支援 XAML 載入路徑、 `Save` 支援 XAML 儲存路徑，而 `Transform` 則提供結合載入路徑和儲存路徑的技術。 `Transform` 可從某個 XAML 結構描述變更為另一個 XAML 結構描述。 本主題摘要說明這些 API 分類，並說明特定方法多載之間的差異。  
  
<a name="load"></a>   
## <a name="load"></a>載入  
 <xref:System.Xaml.XamlServices.Load%2A> 有多種多載會實作載入路徑的完整邏輯。 載入路徑使用某種形式的 XAML，然後輸出 XAML 節點資料流。 這些載入路徑大多數會使用編碼 XML 文字檔形式的 XAML。 不過，您也可以載入一般資料流，或是載入已包含在其他 <xref:System.Xaml.XamlReader> 實作中的預先載入 XAML 來源。  
  
 就大部分的情節而言，最簡單的多載是 <xref:System.Xaml.XamlServices.Load%28System.String%29>。 這個多載具有 `fileName` 參數，也就是包含要載入之 XAML 的文字檔名稱。 這適用於先前已將狀態或資料序列化至本機電腦上的應用程式情節 (例如完全信任應用程式)。 也適用於您正在定義應用程式模型，並想要載入其中一個標準檔案的架構 (這個標準檔案會定義應用程式行為、起始 UI，或其他由架構定義並使用 XAML 的功能)。  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> 具有類似的情節。 如果您要讓使用者選擇要載入的檔案，則這個多載可能會很有用，因為 <xref:System.IO.Stream> 經常是其他可存取檔案系統的 <xref:System.IO> API 的輸出。 或者，您也可以透過非同步下載或其他同樣能夠提供資料流的網路技術，來存取 XAML 來源。 (從資料流或使用者選取的來源載入可能會有安全性隱憂。 如需詳細資訊，請參閱 [XAML Security Considerations](../../../docs/framework/xaml-services/xaml-security-considerations.md)。)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> 和 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> 多載都需要舊版 .NET Framework 的讀取器格式。 若要使用這些多載，您應已建立讀取器執行個體，並使用其 `Create` API 載入相關格式 (文字或 XML) 的 XAML。 如果您已移動其他讀取器中的記錄指標，或使用這些讀取器執行其他作業，則不重要。 <xref:System.Xaml.XamlServices.Load%2A> 中的載入路徑邏輯一律會從根目錄往下處理整個 XAML 輸入。 這些多載的情節可能包括：  
  
-   設計可讓您從現有的 XML 特定文字編輯器，提供簡單 XAML 編輯功能的介面。  
  
-   核心 <xref:System.IO> 的衍生情節，此時您會使用專用讀取器來開啟檔案或資料流。 您的邏輯在嘗試將內容載入為 XAML 之前，會先對其執行初步的檢查或處理。  
  
 您可以載入檔案或資料流，也可以載入 <xref:System.Xml.XmlReader>、 <xref:System.IO.TextReader>或 <xref:System.Xaml.XamlReader> ，這些類別會在與讀取器 API 一起載入時用來包裝您的 XAML 輸入。  
  
 就內部而言，上述每種多載最終都會是 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>，而其中傳遞的 <xref:System.Xml.XmlReader> 可用來建立新的 <xref:System.Xaml.XamlXmlReader>。  
  
 更進階情節適用的 `Load` 簽章是 <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>。 這個簽章可用於下列其中一種情況：  
  
-   您已定義自己的 <xref:System.Xaml.XamlReader>實作。  
  
-   您需要指定不同於預設值的 <xref:System.Xaml.XamlReader> 設定。  
  
 例如，下列任何一項的設定皆屬於非預設設定： <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>、 <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>、 <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>、 <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>、 <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>。 <xref:System.Xaml.XamlServices> 的預設讀取器為 <xref:System.Xaml.XamlXmlReader>。 如果您提供了自己的 <xref:System.Xaml.XamlXmlReader>和設定，下列屬性可用來設定非預設 <xref:System.Xaml.XamlXmlReaderSettings>： <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>、 <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>。  
  
<a name="parse"></a>   
## <a name="parse"></a>Parse  
 <xref:System.Xaml.XamlServices.Parse%2A> 類似 `Load` ，因為它是一個會從 XAML 輸入建立 XAML 節點資料流的載入路徑 API。 不過，在本例中，XAML 輸入會直接以字串的形式提供，其中包含要載入的所有 XAML。 <xref:System.Xaml.XamlServices.Parse%2A> 是較適用於應用程式情節的輕量型方法，對架構情節而言較不適用。 如需詳細資訊，請參閱 <xref:System.Xaml.XamlServices.Parse%2A>。 <xref:System.Xaml.XamlServices.Parse%2A> 實際上只是內含 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> 的包裝 <xref:System.IO.StringReader> 呼叫。  
  
<a name="save"></a>   
## <a name="save"></a>Save  
 <xref:System.Xaml.XamlServices.Save%2A> 有多種多載會實作儲存路徑。 所有 <xref:System.Xaml.XamlServices.Save%2A> 方法都會接受物件圖形做為輸入，然後產生資料流、檔案或 <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> 執行個體等形式的輸出。  
  
 輸入物件必須是某個物件表示的根物件。 這可以是商務物件的單一根物件、UI 情節中頁面之物件樹狀目錄的根目錄、設計工具中的工作編輯介面，或是其他適用於情節的根物件概念。  
  
 在許多情節中，您所儲存的物件樹狀目錄，都與用來載入 XAML 的原始作業相關 (不論是透過 <xref:System.Xaml.XamlServices.Load%2A>，還是透過架構 / 應用程式模型所實作的其他 API 載入)。 物件樹狀目錄中可能會出現差異，其原因包括狀態變更、應用程式擷取到使用者在執行階段做出的設定變更、由於應用程式是 XAML 設計介面而影響的 XAML 變更等等。無論是否有所變更，從標記載入 XAML 再儲存 XAML，然後比較兩個 XAML 標記格式的這個概念，有時會被視為 XAML 的反覆存取表示。  
  
 儲存和序列化以標記形式設定之複雜物件的挑戰，在於如何能夠完整表示而不遺漏資訊，同時又不致過於繁瑣而使 XAML 不易閱讀。 再者，不同的 XAML 客戶對於如何拿捏此一平衡，也有不同的定義或期望。 <xref:System.Xaml.XamlServices.Save%2A> API 就是該平衡的其中一種定義。 <xref:System.Xaml.XamlServices.Save%2A> API 使用可用的 XAML 結構描述內容，以及 <xref:System.Xaml.XamlType>、 <xref:System.Xaml.XamlMember>和其他 XAML 內建和 XAML 類型系統概念的預設 CLR 特性，來判斷特定 XAML 節點資料流建構在重新儲存成標記時可進行最佳化的位置。 例如，<xref:System.Xaml.XamlServices> 儲存路徑可使用以 CLR 為基礎的預設 XAML 結構描述內容，來解析物件的 <xref:System.Xaml.XamlType>可判斷 <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>；接著可在將屬性寫入物件的 XAML 內容時，省略屬性項目標記。  
  
<a name="transform"></a>   
## <a name="transform"></a>轉換  
 <xref:System.Xaml.XamlServices.Transform%2A> 會藉由將載入路徑和儲存路徑連結成單一作業，來轉換 XAML。 <xref:System.Xaml.XamlReader> 和 <xref:System.Xaml.XamlWriter>則可能會使用不同的結構描述內容或支援類型系統，而影響產生之 XAML 的轉換方式。 這適用於各種轉換作業。  
  
 如果作業需要檢查 XAML 節點資料流中的每個節點，您通常不會使用 <xref:System.Xaml.XamlServices.Transform%2A>。 相反地，您需要定義自己的載入路徑-儲存路徑作業序列，並插入自己的邏輯。 請在其中一個路徑中，在您自己的節點迴圈周圍使用 XAML 讀取器/XAML 寫入器配對。 例如，使用 <xref:System.Xaml.XamlXmlReader> 載入初始 XAML，再以後續的 <xref:System.Xaml.XamlXmlReader.Read%2A> 呼叫逐步執行至各節點。 在 XAML 節點資料流層級上運作時，您現在可以調整個別節點 (類型、成員、其他節點) 以套用轉換，或讓節點保持原狀。 接著，您可以將節點繼續傳送至 `Write` 的相關 <xref:System.Xaml.XamlObjectWriter> API 並寫出物件。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xaml.XamlObjectWriter>  
 <xref:System.Xaml.XamlServices>  
 [XAML Services](../../../docs/framework/xaml-services/index.md)
