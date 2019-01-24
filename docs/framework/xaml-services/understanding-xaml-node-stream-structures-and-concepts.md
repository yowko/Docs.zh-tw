---
title: 認識 XAML 節點資料流結構和概念
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: d237aa83a6bd1c6c68f96aa4fa58a88cfa23c2c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510139"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>認識 XAML 節點資料流結構和概念
XAML 讀取器和 XAML 寫入器在 .NET Framework XAML 服務中實作，根據 XAML 節點資料流的設計概念。 XAML 節點資料流是一組 XAML 節點的概念化。 在此概念化中，XAML 處理器會逐步查核 XAML 中的節點關聯性結構，一次一個 XAML。 在任何時候，只能有一個目前的記錄或目前的位置存在於開啟的 XAML 節點資料流中，而應用程式開發介面的許多層面只會報告從該位置取得的資訊。 XAML 節點資料流中的目前節點可以描述成物件、成員或值。 若將 XAML 視為 XAML 節點資料流，XAML 讀取器可以與 XAML 寫入器進行通訊，並可讓程式在有關 XAML 的載入路徑或儲存路徑作業期間，檢視、變更 XAML 節點資料流的內容，或與其互動。 XAML 讀取器和寫入器應用程式開發介面的設計和 XAML 節點資料流概念，類似先前相關讀取器和寫入器的設計和概念，例如 [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] ，以及 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 類別。 本主題討論 XAML 節點資料流概念，並說明如何撰寫在 XAML 節點層級與 XAML 表示法互動的常式。  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>正在將 XAML 載入 XAML 讀取器  
 基底 <xref:System.Xaml.XamlReader> 類別不會宣告用來將初始 XAML 載入 XAML 讀取器中的特定技術。 反而是衍生的類別會宣告並實作載入技術，包括其用於 XAML 之輸入來源的一般特性和條件約束。 例如， <xref:System.Xaml.XamlObjectReader> 會讀取物件圖形，從代表根或基底之單一物件的輸入來源開始。 然後 <xref:System.Xaml.XamlObjectReader> 會從物件圖形產生 XAML 節點資料流。  
  
 最著名的 .NET Framework XAML 服務定義 <xref:System.Xaml.XamlReader> 子類別是 <xref:System.Xaml.XamlXmlReader>。 <xref:System.Xaml.XamlXmlReader> 會載入初始的 XAML，其方法是直接透過資料流或檔案路徑，或間接透過相關的讀取器類別 (例如 <xref:System.IO.TextReader>)，來載入文字檔案。 <xref:System.Xaml.XamlReader> 載入之後，即可視為包含 XAML 輸入來源的全部內容。 不過，因為有設計 <xref:System.Xaml.XamlReader> 基底應用程式開發介面，所以讀取器是在與 XAML 的單一節點互動。 第一次載入時，您遇到的第一個節點會是 XAML 的根目錄及其開始物件。  
  
### <a name="the-xaml-node-stream-concept"></a>XAML 節點資料流概念  
 如果您通常較為熟悉以 DOM、樹狀目錄象徵物或查詢式手法來存取 XML 架構的技術，下面的方法將有助於將 XAML 節點資料流概念化。 假設載入的 XAML 是 DOM 或樹狀結構，其中每個可能的節點都是全部展開，然後以線性方式呈現。 當您在節點中向前推進時，您可能會在 DOM 的相關層級中來回「進」、「出」，但 XAML 節點資料流不會明確地保留追蹤，因為這些層級概念與節點資料流無關。 節點資料流具有「目前」位置，但除非您自己已經將資料流的其他部分儲存成參考，否則，除了目前的節點位置以外，您將看不見節點資料流的所有其他層面。  
  
 XAML 節點資料流概念有一個值得注意的優點，如果您通過了整個節點資料流，則可確定您已處理整個的 XAML 表示；不需要擔心用來處理資訊的查詢、DOM 作業或某些其他非線性方法遺漏了完整 XAML 表示的某些部分。 基於這個理由，XAML 節點資料流表示適合用來連接 XAML 讀取器和 XAML 寫入器，也適合用來提供一個系統，讓您可以在其中插入您自己處理序，以在 XAML 處理作業的讀取和寫入階段之間運作。 在許多情況下，相對於可能出現在原始程式文字、二進位或物件圖形中的排列方式，XAML 讀取器會將 XAML 節點資料流中的節點排列順序謹慎地最佳化，或是重新排列。 此行為是為了強制執行 XAML 處理架構，如此一來，XAML 寫入器就永遠不會在節點資料流中其必須「返回」的位置。 在理想的情況下，所有 XAML 寫入作業都應該能夠依據結構描述內容以及節點資料流的目前位置來運作。  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>基本讀取節點迴圈  
 用來檢查 XAML 節點資料流的基本讀取節點迴圈包含下列概念。 基於本主題中討論的節點迴圈，假設您正在使用 <xref:System.Xaml.XamlXmlReader>來閱讀以文字為基礎、人類可讀的 XAML 檔案。 本節中的連結指向 <xref:System.Xaml.XamlXmlReader>所實作的特定 XAML 節點迴圈應用程式開發介面。  
  
-   請確定您不是在 XAML 節點資料流結尾 (檢查 <xref:System.Xaml.XamlXmlReader.IsEof%2A>，或使用 <xref:System.Xaml.XamlXmlReader.Read%2A> 傳回值)。 如果您是在資料流結尾，那裡並沒有目前的節點，您應該要結束。  
  
-   呼叫 <xref:System.Xaml.XamlXmlReader.NodeType%2A>，以檢查 XAML 節點資料流目前公開的節點類型為何。  
  
-   如果您有直接連線的相關 XAML 物件寫入器，您通常會在這時候呼叫 <xref:System.Xaml.XamlWriter.WriteNode%2A> 。  
  
-   根據被報告為目前節點或目前記錄的 <xref:System.Xaml.XamlNodeType> ，呼叫下列其中一項，以取得節點內容的相關資訊：  
  
    -   針對 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 或 <xref:System.Xaml.XamlNodeType.StartMember> 的 <xref:System.Xaml.XamlNodeType.EndMember>，呼叫 <xref:System.Xaml.XamlXmlReader.Member%2A> ，以取得成員的 <xref:System.Xaml.XamlMember> 相關資訊。 請注意，成員可能是 <xref:System.Xaml.XamlDirective>，因此不一定會是上述物件的傳統類型定義成員。 例如，套用至物件的 `x:Name` 似乎是 XAML 成員，其中 <xref:System.Xaml.XamlMember.IsDirective%2A> 為 true，而成員的 <xref:System.Xaml.XamlMember.Name%2A> 為 `Name`，還有其他屬性指出這個指示詞在 XAML 語言 XAML 命名空間之下。  
  
    -   針對 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 或 <xref:System.Xaml.XamlNodeType.StartObject> 的 <xref:System.Xaml.XamlNodeType.EndObject>，呼叫 <xref:System.Xaml.XamlXmlReader.Type%2A> ，以取得物件的 <xref:System.Xaml.XamlType> 相關資訊。  
  
    -   針對 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 的 <xref:System.Xaml.XamlNodeType.Value>，呼叫 <xref:System.Xaml.XamlXmlReader.Value%2A>。 唯有當節點對成員是某個值的最簡單運算式，或對物件是初始化文字時，該節點才會是一個值 (不過，您應該要注意類型轉換行為，本主題後續章節將會說明)。  
  
    -   針對 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 的 <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>，呼叫 <xref:System.Xaml.XamlXmlReader.Namespace%2A> ，以取得命名空間節點的命名空間資訊。  
  
-   呼叫 <xref:System.Xaml.XamlXmlReader.Read%2A> ，使 XAML 讀取器前進至 XAML 節點資料流中的下一個節點，然後再重複那些步驟。  
  
 .NET Framework XAML 服務 XAML 讀取器提供的 XAML 節點資料流，永遠都會提供所有可能節點的完整、深層周遊。 XAML 節點迴圈的一般流程控制技術，包括定義 `while (reader.Read())`內的主體，以及在節點迴圈中每個節點的 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 上切換。  
  
 如果節點資料流位於檔案結尾，則目前節點為 null。  
  
 使用讀取器和寫入器的最簡單迴圈，類似下列範例。  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 這個載入路徑 XAML 節點迴圈的基本範例以透通方式連接 XAML 讀取器和 XAML 寫入器，所執行的動作和您使用 <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType> 來進行時並無不同。 但是這個基本結構到時會展開，以套用至您的讀取或寫入情節。 部分可能的情節如下：  
  
-   在 <xref:System.Xaml.XamlXmlReader.NodeType%2A>上切換。 依據所讀取的節點類型，執行不同的動作。  
  
-   在所有案例中，都不要呼叫 <xref:System.Xaml.XamlWriter.WriteNode%2A> 。 只在某些 <xref:System.Xaml.XamlWriter.WriteNode%2A> 案例中，才呼叫 <xref:System.Xaml.XamlXmlReader.NodeType%2A> 。  
  
-   特定節點類型內的邏輯，分析該節點的細節，並採取行動。 例如，您只能撰寫來自特定 XAML 命名空間的物件，然後卸除或延遲不是來自該 XAML 命名空間的任何物件。 或者，如果您的 XAML 系統不支援將任何 XAML 指示詞當做成員處理程序的一部分，您可以卸除或重新處理該 XAML 指示詞。  
  
-   定義會覆寫 <xref:System.Xaml.XamlObjectWriter> 方法的自訂 `Write*` ，可能會執行略過 XAML 結構描述內容的類型對應。  
  
-   建構 <xref:System.Xaml.XamlXmlReader> 來使用非預設 XAML 結構描述內容，以便讀取器和寫入器都能使用 XAML 行為中的自訂差異。  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>超越節點迴圈概念的 XAML 存取  
 除了 XAML 節點迴圈之外，還有其他處理 XAML 表示的可能方式。 例如，可能存在著可以讀取索引節點的 XAML 讀取器，或特別是直接以 `x:Name`、以 `x:Uid`或透過其他識別項存取節點的 XAML 讀取器。 .NET Framework XAML 服務沒有提供完整的實作，但會透過服務和支援類型來提供建議的模式。 如需詳細資訊，請參閱 <xref:System.Xaml.IXamlIndexingReader> 與 <xref:System.Xaml.XamlNodeList>。  
  
> [!TIP]
>  Microsoft 也有生產名為 Microsoft XAML Toolkit 的 Out-of-Band 版本。 這個 Out-of-Band 版本仍在其發行前階段。 不過，如果您願意使用發行前元件，Microsoft XAML Toolkit 有提供一些有趣的資源，可用於 XAML 工具和 XAML 的靜態分析。 Microsoft XAML Toolkit 包含 XAML DOM 應用程式開發介面、FxCop 分析的支援，以及適用於 Silverlight 的 XAML 結構描述內容。 如需詳細資訊，請參閱 [Microsoft XAML Toolkit](https://code.msdn.microsoft.com/XAML)。  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>使用目前的節點  
 使用 XAML 節點迴圈的大部分情節不會只讀取節點。 大部分情節都會處理目前的節點，並且一次一個，將每個節點傳遞至 <xref:System.Xaml.XamlWriter>的實作。  
  
 一般載入路徑情節為 <xref:System.Xaml.XamlXmlReader> 產生 XAML 節點資料流；根據您的邏輯和 XAML 結構描述內容來處理 XAML 節點；將節點傳遞至 <xref:System.Xaml.XamlObjectWriter>。 然後您要將結果物件圖形整合至您的應用程式或架構中。  
  
 一般儲存路徑情節為 <xref:System.Xaml.XamlObjectReader> 讀取物件圖形；處理個別 XAML 節點； <xref:System.Xaml.XamlXmlWriter> 將序列化結果輸出為 XAML 文字檔。 關鍵在於路徑和情節都是一次只能處理一個 XAML 節點，而 XAML 節點可以用 XAML 類型系統和 .Net Framework XAML 服務應用程式開發介面所定義的標準化方式來處理。  
  
### <a name="frames-and-scope"></a>框架和範圍  
 XAML 節點迴圈會以線性方式處理 XAML 節點資料流。 節點資料流會周遊至物件中，以及包含其他物件的成員中等等。 實作框架和堆疊概念來追蹤 XAML 節點資料流內的範圍，通常會很有用。 特別是當您處於節點資料流中，並積極加以調整時，更是好用。 如果從 DOM 的觀點來看 XAML 節點結構，您實作為節點迴圈邏輯一部分的框架和堆疊支援，會隨著您深入該結構，計算 `StartObject` (或 `GetObject`) 和 `EndObject` 範圍。  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>周遊及進入物件節點  
 當 XAML 讀取器開啟節點資料流時，其中的第一個節點，就是根物件的開始物件節點。 根據定義，此物件一律為單一物件節點，沒有對等項目。 在任何真實世界的 XAML 範例中，根物件的定義為具有保存多個物件的一或多個屬性，而這些屬性具有成員節點。 然後成員節點有一或多個物件節點，但也可能會在值節點中終止。 根物件通常會定義 XAML 名稱範圍，這些名稱範圍會藉由語法指派成 XAML 文字標記中的屬性，但會對應至 XAML 節點資料流表示中的 `Namescope` 節點類型。  
  
 請考量下列 XAML 範例 (這是任意 XAML，不受 .NET Framework 中現有的類型支援)。 假設在此物件模型中， `FavorCollection` 是 `List<T>` 的 `Favor`， `Balloon` 和 `NoiseMaker` 可指派給 `Favor`， `Balloon.Color` 屬性受 `Color` 物件支援 (方法類似 WPF 將色彩定義為已知的色彩名稱)，而 `Color` 支援屬性語法的類型轉換器。  
  
|XAML 標記|產生的 XAML 節點資料流|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace` 的 `Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject` 的 `Party`|  
|`<Party.Favors>`|`StartMember` 的 `Party.Favors`|  
||隱含`StartObject` 的 `FavorCollection`節點|  
||隱含`StartMember` 項目屬性的 `FavorCollection` 節點。|  
|`<Balloon`|`StartObject` 的 `Balloon`|  
|`Color="Red"`|`StartMember` 的 `Color`<br /><br /> 屬性值字串`Value` 的 `"Red"`節點<br /><br /> `EndMember` 的 `Color`|  
|`HasHelium="True"`|`StartMember` 的 `HasHelium`<br /><br /> 屬性值字串`Value` 的 `"True"`節點<br /><br /> `EndMember` 的 `HasHelium`|  
|`>`|`EndObject` 的 `Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` 的 `NoiseMaker`<br /><br /> `StartMember` 的 `_Initialization`<br /><br /> 初始值字串`Value` 的 `"Loudest"`節點<br /><br /> `EndMember` 的 `_Initialization`<br /><br /> `EndObject` 的 `NoiseMaker`|  
||隱含`EndMember` 項目屬性的 `FavorCollection` 節點。|  
||隱含`EndObject` 的 `FavorCollection`節點|  
|`</Party.Favors>`|`EndMember` 的 `Favors`|  
|`</Party>`|`EndObject` 的 `Party`|  
  
 在 XAML 節點資料流中，您可以依賴下列行為：  
  
-   如果 `Namespace` 節點存在，會將它加入以 `StartObject` 宣告 XAML 命名空間之 `xmlns`前面的資料流。 再看一次包含 XAML 和範例節點資料流的上表。 注意 `StartObject` 和 `Namespace` 節點似乎調換的情形，以及其於文字標記中的宣告位置。 這是具有代表性的行為，其中命名空間節點一律出現在節點資料流中，套用該命名空間節點的節點前面。 這種設計的目的是，命名空間資訊對物件寫入器而言非常重要，在物件寫入器嘗試執行類型對應或者處理物件之前，必須先知道該資訊。 將 XAML 命名空間資訊放在資料流中其應用程式範圍的前面，要一律以其呈現的順序來處理節點資料流，就會比較容易。  
  
-   基於上述考量，在真實世界的大部分標記案例中，從頭開始周遊節點時 (不是從根目錄的 `Namespace` )，您都會先讀取一或多個 `StartObject` 節點。  
  
-   `StartObject` 節點後面可以接 `StartMember`、 `Value`，或緊接著 `EndObject`。 它後面永遠不會緊接著另一個 `StartObject`。  
  
-   `StartMember` 後面可以接 `StartObject`、 `Value`，或緊接著 `EndMember`。 如果成員中的值應該是來自父物件的現有值，而不是會具現化新值的 `GetObject`，則後面可以接 `StartObject` 。 它後面也可以接 `Namespace` 節點，這會套用到後續的 `StartObject`。 它後面永遠不會緊接著另一個 `StartMember`。  
  
-   `Value` 節點代表該值本身；沒有 "EndValue"。 它後面只能接 `EndMember`。  
  
    -   可能被建構使用之物件的 XAML 初始文字，不會產生「物件-值」結構。 而是會針對名為 `_Initialization` 的成員，建立專用成員節點。 而該成員節點會包含初始值字串。 如果它存在的話， `_Initialization` 永遠是第一個 `StartMember`。 `_Initialization` 可能會限定在具有 XAML 語言的 XAML 名稱範圍的某些 XAML 服務表示中，以釐清 `_Initialization` 不支援類型中定義的屬性。  
  
    -   「成員-值」組合代表該值的屬性設定。 可能最後會有值轉換器一起來處理這個值，而這個值是純文字字串。 不過，在 XAML 物件寫入器處理此節點資料流之前，不會評估這一點。 XAML 物件寫入器擁有必要的 XAML 結構描述內容、類型系統對應，以及值轉換所需的其他支援。  
  
-   `EndMember` 節點後面可以接著後續成員的 `StartMember` 節點，或是成員擁有者的 `EndObject` 節點。  
  
-   `EndObject` 節點後面可以接著 `EndMember` 節點。 在集合的項目中，物件是對等的情況下，它後面可以接著 `StartObject` 節點。 或者它後面可以接 `Namespace` 節點，這會套用到後續的 `StartObject`。  
  
    -   針對關閉整個節點資料流這種特殊狀況，根目錄的 `EndObject` 的後面沒有接任何項目；讀取器現在是檔案結尾，而 <xref:System.Xaml.XamlReader.Read%2A> 會傳回 `false`。  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>值轉換器和 XAML 節點資料流  
 值轉換器是下列項目的泛稱：標記延伸、類型轉換器 (包括值序列化程式)，或是透過 XAML 類型系統報告為值轉換器的另一個專用類別。 在 XAML 節點資料流中，類型轉換器的用法和標記延伸的用法有非常不同的表示方式。  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>XAML 節點資料流中的類型轉換器  
 最後會導致使用類型轉換器的屬性集，會在 XAML 節點資料流中報告為成員的值。 XAML 節點資料流不會嘗試產生類型轉換器執行個體物件，並將值傳遞給它。 使用類型轉換器的轉換實作時，需要叫用 XAML 結構描述內容，並將其用於類型對應。 即使是判斷應該使用哪一個類型轉換器類別來處理該值，都間接需要 XAML 結構描述內容。 當您使用預設 XAML 結構描述內容時，可從 XAML 類型系統取得該資訊。 如果您在連接至 XAML 寫入器之前，需要 XAML 節點資料流層級的類型轉換器類別資訊，您可以從所設定之成員的 <xref:System.Xaml.XamlMember> 資訊取得該資訊。 要不然，類型轉換器輸入應該會以純文字值，保留在 XAML 節點資料流中，直到執行完需要類型對應系統和 XAML 結構描述內容的其餘作業，例如 XAML 物件寫入器建立物件的作業。  
  
 比方說，請考慮下列類別定義大綱及其 XAML 用法：  
  
```  
public class BoardSizeConverter : TypeConverter {  
  //converts from string to an int[2] by splitting on an "x" char  
}  
public class GameBoard {  
  [TypeConverter(typeof(BoardSizeConverter))]  
  public int[] BoardSize; //2x2 array, initialization not shown  
}  
```  
  
```xaml  
<GameBoard BoardSize="8x8"/>  
```  
  
 這種用法的 XAML 節點資料流文字表示，無法以下列方式表示：  
  
 `StartObject` 搭配 <xref:System.Xaml.XamlType> 表示 `GameBoard`  
  
 `StartMember` 搭配 <xref:System.Xaml.XamlMember> 表示 `BoardSize`  
  
 `Value` 節點，包含文字字串 "`8x8`"  
  
 `EndMember` 符合 `BoardSize`  
  
 `EndObject` 符合 `GameBoard`  
  
 請注意，這個節點資料流中沒有類型轉換器執行個體。 但是您可以在 `BoardSize` 的 <xref:System.Xaml.XamlMember> 上呼叫 <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType>，以取得類型轉換器資訊。 如果您有有效的 XAML 結構描述內容，您也可以從 <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>取得執行個體，以叫用轉換器方法。  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML 節點資料流中的標記延伸  
 標記延伸的使用會在 XAML 節點資料流中報告為成員中的物件節點，其中該物件代表標記延伸執行個體。 因此，在節點資料流表示中使用標記延伸，會比使用類型轉換器更明確地顯示，而且附帶更多資訊。 <xref:System.Xaml.XamlMember> 資訊不會告訴您有關標記延伸的任何資訊，因為該用法依情況而定，而且在每個可能的標記案例中各不相同；它不像使用類型轉換器的案例那樣是依每個類型或成員專用和隱含。  
  
 即使是在 XAML 文字標記中，以屬性形式來使用標記延伸 (通常會這樣)，還是以標記延伸的節點資料流表示做為物件節點。 使用明確物件項目表單的標記延伸用法會以相同的方式處理。  
  
 在標記延伸物件節點中，可能會有該標記延伸的成員。 XAML 節點資料流表示會保留該標記延伸的使用，不論是位置參數用法或具有明確具名參數的用法。  
  
 若為位置參數用法，XAML 節點資料流會包含 XAML 語言定義屬性 `_PositionalParameters` ，以記錄該用法。 這個屬性為泛型 <xref:System.Collections.Generic.List%601> ，具有 <xref:System.Object> 條件約束。 條件約束是物件，而不是字串，因為理論上位置參數用法可能會在其中包含巢狀標記延伸用法。 若要從該用法存取位置參數，您可以逐一查看清單，並將索引子用於個別清單值。  
  
 若為具名參數用法，每個具名參數都會表示為節點資料流中該名稱的成員節點。 成員值不一定是字串，因為可能會有巢狀標記延伸用法。  
  
 尚未叫用來自標記延伸的`ProvideValue` 。 不過，如果您連接 XAML 讀取器和 XAML 寫入器，導致當您在節點資料流中檢查時，在標記延伸節點上叫用 `WriteEndObject` ，就會叫用它。 基於這個理由，您通常會需要有為了在載入路徑上形成物件圖形而使用的相同 XAML 結構描述內容。 否則，來自任何標記延伸的 `ProvideValue` 都可能在這裡擲回例外狀況，因為它沒有預期的服務可用。  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML 節點資料流中的 XAML 和 XML 語言定義成員  
 因為 XAML 讀取器的解譯和慣例，會將特定成員導入 XAML 節點資料流中，而不是透過明確的 <xref:System.Xaml.XamlMember> 查閱或建構。 這些成員通常是 XAML 指示詞。 在某些情況下，它是讀取將指示詞導入 XAML 節點資料流中之 XAML 的動作。 換句話說，原始輸入 XAML 文字並沒有明確指定成員指示詞，但 XAML 讀取器會插入指示詞，以在 XAML 節點資料流中的結構化 XAML 慣例和報告資訊遺失之前，滿足該資訊。  
  
 下列清單指出 XAML 讀取器應該要導入指示詞 XAML 成員節點的所有案例，以及如何在 .NET Framework XAML 服務實作中識別該成員節點。  
  
-   **物件節點的初始文字：** 此成員節點的名稱是`_Initialization`，它代表 XAML 指示詞，且其定義在 XAML 語言 XAML 命名空間。 您可以從 <xref:System.Xaml.XamlLanguage.Initialization%2A>取得其靜態實體。  
  
-   **標記延伸的位置參數：** 此成員節點的名稱是`_PositionalParameters`，且其定義在 XAML 語言 XAML 命名空間。 它一律包含物件的泛型清單，每個物件都是位置參數，以 `,` 分隔符號字元預先分隔，和輸入 XAML 中所提供的一樣。 您可以從 <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>取得位置參數指示詞的靜態實體。  
  
-   **未知的內容：** 此成員節點的名稱是`_UnknownContent`。 嚴格來說，它是 <xref:System.Xaml.XamlDirective>，且其定義在 XAML 語言 XAML 命名空間中。 如果 XAML 物件項目包含來源 XAML 中的內容，但是在目前可用的 XAML 結構描述內容之下，無法判斷任何內容屬性，則會將這個指示詞當作 Sentinel 使用。 若要在 XAML 節點資料流中偵測此情況，您可以檢查是否有名為 `_UnknownContent` 的成員。 如果在載入路徑 XAML 節點資料流中，沒有採取任何其他動作，當它遇到任何物件上的 <xref:System.Xaml.XamlObjectWriter> 成員，預設 `WriteEndObject` 就會在所嘗試的 `_UnknownContent` 上擲回。 預設 <xref:System.Xaml.XamlXmlWriter> 不會擲回，並且會將成員視為隱含。 您可以從 `_UnknownContent` 取得 <xref:System.Xaml.XamlLanguage.UnknownContent%2A>的靜態實體。  
  
-   **集合的集合屬性：** 雖然用於 XAML 之集合類別的支援 CLR 類型，通常會有專用具名屬性可保存集合項目，但是在支援類型解析之前，XAML 類型系統並不知道該屬性。 相反地，XAML 節點資料流會導入 `Items` 預留位置，做為集合 XAML 類型的成員。 在 .NET Framework XAML 服務實作中，這個指示詞/成員在節點資料流中的名稱為 `_Items`。 這個指示詞的常數可以從 <xref:System.Xaml.XamlLanguage.Items%2A>取得。  
  
     注意：XAML 節點資料流可能包含 Items 屬性，而依據支援類型解析和 XAML 結構描述內容，其中的項目是無法剖析的。 例如，套用至物件的  
  
-   **XML 定義的成員：** XML 定義`xml:base`，`xml:lang`並`xml:space`成員皆會回報為名為 XAML 指示詞`base`， `lang`，和`space`在.NET Framework XAML 服務實作。 這些成員的命名空間是 XML 命名空間 `http://www.w3.org/XML/1998/namespace`。 您可以從 <xref:System.Xaml.XamlLanguage>取得每個成員的常數。  
  
## <a name="node-order"></a>節點順序  
 在某些情況下， <xref:System.Xaml.XamlXmlReader> 會變更 XAML 節點資料流中的 XAML 節點順序，不同於在標記中檢視或當做 XML 處理時，所出現的節點順序。 這麼做是為了排列節點，讓 <xref:System.Xaml.XamlObjectWriter> 可以用僅限順向的方式來處理節點資料流。  在 .NET Framework XAML 服務中，XAML 讀取器會重新排列節點，而不會將這項工作留給 XAML 寫入器，如此可以讓節點資料流的 XAML 物件寫入器消費者獲得最佳化效能。  
  
 某些指示詞的目的，是為了在從物件項目建立物件時，提供更多資訊。 這些指示詞為： `Initialization`、 `PositionalParameters`、 `TypeArguments`、 `FactoryMethod`、 `Arguments`。 .NET Framework XAML 服務 XAML 讀取器會嘗試將這些指示詞當做節點資料流中的第一個成員，接在物件的 `StartObject`後面，原因將會在下一節中說明。  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter 行為和節點順序  
 `StartObject` 的 <xref:System.Xaml.XamlObjectWriter> 不一定是要 XAML 物件寫入器立即建構物件執行個體的信號。 XAML 包含數種語言功能，可讓您使用其他輸入來初始化物件，並且不要完全依賴叫用預設建構函式來產生初始物件，然後只設定屬性。 這些功能包括： <xref:System.Windows.Markup.XamlDeferLoadAttribute>、初始文字、 [x:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md)、標記延伸的位置參數、Factory 方法，以及相關聯的 [x:Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) 節點 (XAML 2009)。 這些案例每個都會延遲實際的物件建構，而且因為節點資料流已重新排列，所以 XAML 物件寫入器可以依賴每當所遇到的開始成員不是特別用於該物件類型的建構指示詞時，就會實際建構執行個體的行為。  
  
### <a name="getobject"></a>GetObject  
 `GetObject` 表示 XAML 節點，其中，XAML 物件寫入器並不是要建構新的物件，而是應該要取得物件的包含屬性值。 在支援類型的物件模型中，當包含屬性是刻意唯讀時，在 XAML 節點資料流中遇到 `GetObject` 節點這種一般情況，會發生於集合物件或字典物件。 在此情節中，通常會由擁有者類型的初始化邏輯來建立及初始化集合或字典 (通常是空的)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xaml.XamlObjectReader>
- [XAML Services](../../../docs/framework/xaml-services/index.md)
- [XAML 命名空間](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
