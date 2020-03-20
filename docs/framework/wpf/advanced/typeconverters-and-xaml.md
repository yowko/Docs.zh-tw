---
title: TypeConverter 和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187301"
---
# <a name="typeconverters-and-xaml"></a>TypeConverter 和 XAML
本主題介紹將字串的類型轉換當成一般 XAML 語言功能的目的。 在 .NET 框架中<xref:System.ComponentModel.TypeConverter>，類作為託管自訂類的實現的一部分服務于特定用途，該類可用作 XAML 屬性用法中的屬性值。 如果編寫自訂類，並且希望類的實例可用作 XAML 可設置屬性值，則可能需要將 應用<xref:System.ComponentModel.TypeConverterAttribute>到類、編寫自訂<xref:System.ComponentModel.TypeConverter>類或兩者兼而有之。  

## <a name="type-conversion-concepts"></a>類型轉換概念  
  
### <a name="xaml-and-string-values"></a>XAML 和字串值  
 在 XAML 檔案中設定屬性值時，該值的初始類型是純文字的字串。 甚至其他基元，如<xref:System.Double>最初文本字串到XAML處理器。  
  
 XAML 處理器需要兩項資訊才能處理屬性值。 第一項資訊是正在設定之屬性的實值類型。 任何定義屬性值並在 XAML 中處理的字串最後必須轉換或解析成該類型的值。 如果值是 XAML 剖析器可理解的基本類型 (例如數值)，則會嘗試直接轉換字串。 如果值是一個列舉，則用來檢查名稱的字串會符合該列舉中的具名常數。 如果值不是剖析器所辨識的基本類型，也不是列舉，則上述類型必須能夠根據已轉換的字串提供類型的執行個體或值。 您可以藉由指定類型轉換器類別來完成此動作。 類型轉換子實際上是一個 Helper 類別，可用於提供另一個類別的值，這兩者均適用於 XAML 案例，可能也適用於利用 .NET 程式碼進行程式碼呼叫。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>在 XAML 中使用現有的類型轉換行為  
 根據您對基礎 XAML 概念的熟悉程度而定，您可能已經在基本應用程式 XAML 中使用類型轉換行為而不自知。 例如，WPF 從字面上定義數百個屬性，這些屬性具有類型<xref:System.Windows.Point>的值 。 是<xref:System.Windows.Point>描述二維座標空間中的座標的值，它實際上只有兩個重要屬性：<xref:System.Windows.Point.X%2A>和<xref:System.Windows.Point.Y%2A>。 在 XAML 中指定點時，將它指定為在 和<xref:System.Windows.Point.X%2A>提供<xref:System.Windows.Point.Y%2A>的值之間具有分隔符號（通常是逗號）的字串。 例如：`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`。  
  
 即使是這種簡單的類型<xref:System.Windows.Point>和它在XAML的簡單用法也涉及一個類型轉換器。 在這種情況下，這是類<xref:System.Windows.PointConverter>。  
  
 類<xref:System.Windows.Point>級別定義的類型轉換器簡化了採用<xref:System.Windows.Point>的所有屬性的標記用法。 若未在此處使用類型轉換器，您就需要針對先前所示的同一個範例使用下列更多較為詳細的標記：  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 是否要使用類型轉換字串或較為詳細的對等語法，通常是編碼樣式的選擇。 您的 XAML 工具工作流程可能也會影響值的設定方式。 一些 XAML 工具傾向於發出最詳細格式的標記，因為較容易反覆存取設計工具檢視或它自己的序列化機制。  
  
 現有類型轉換器通常可以通過檢查類（或屬性）是否存在應用<xref:System.ComponentModel.TypeConverterAttribute>的 ，在 WPF 和 .NET 框架類型上發現。 這個屬性將基於 XAML 用途以及其他可能的用途，針對該類型的值，為支援類型轉換器的類別命名。  
  
### <a name="type-converters-and-markup-extensions"></a>類型轉換器和標記延伸  
 標記延伸和類型轉換器會根據 XAML 處理器行為和套用它們的案例來填滿正交角色。 儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性類型轉換行為在標記延伸實作中通常不會遭到檢查。 換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，也不會在該字串上叫用套用至特定屬性或屬性值類型的類型轉換行為。一般來說，標記延伸的目的是在未涉及任何類型轉換器的情況下，處理字串並傳回物件。  
  
 需要標記延伸而不是類型轉換器的一個常見情況是參考現有的物件。 無狀態類型轉換器充其量只能產生新的執行個體，但這可能不是令人滿意的情況。 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
### <a name="native-type-converters"></a>原生類型轉換器  
 在 XAML 剖析器中的 WPF 和 .NET Framework 實作中，有些特定類型具有原生類型轉換處理，但卻不是依慣例會被視為基本類型的類型。 這類類型的範例是 <xref:System.DateTime>。 其原因基於 .NET 框架體系結構的工作原理：類型<xref:System.DateTime>在 mscorlib 中定義，mscorlib 是 .NET 中最基本的庫。 <xref:System.DateTime>不允許將屬性歸因於來自引入依賴項的另一個程式集（<xref:System.ComponentModel.TypeConverterAttribute>來自 System），因此不支援通過歸因進行通常的類型轉換器發現機制。 而是 XAML 剖析器會有一份需要這類原生處理的類型清單，這些類型的處理方式會與真正基本類型的處理方式類似 （在這種情況下，<xref:System.DateTime>涉及對<xref:System.DateTime.Parse%2A>的調用。  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>實作類型轉換器  
  
### <a name="typeconverter"></a>TypeConverter  
 在之前<xref:System.Windows.Point>給出的示例中，提到了類<xref:System.Windows.PointConverter>。 對於 XAML 的 .NET 實現，用於 XAML 的所有類型轉換器都是派生自基類 的類<xref:System.ComponentModel.TypeConverter>。 類<xref:System.ComponentModel.TypeConverter>存在於 XAML 存在之前的 .NET 框架版本中;其原始用法之一是為視覺化設計器中的屬性對話方塊提供字串轉換。 對於 XAML，將<xref:System.ComponentModel.TypeConverter>的角色擴展為包括用於用於對字串和從字串轉換的基類，這些轉換支援分析字串屬性值，並可能將特定物件屬性的運行時值處理回字串，作為屬性進行序列化。  
  
 <xref:System.ComponentModel.TypeConverter>定義四個與轉換字串和轉換字串相關的成員，以便進行 XAML 處理目的：  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 其中最重要的方法是<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>。 這個方法會將輸入字串轉換為所需的物件類型。 嚴格地說，<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>該方法可以實現，將更廣泛的類型轉換為轉換器的預期目標型別，從而服務于超出 XAML 的目的，例如支援運行時轉換，但對於 XAML 目的，只有代碼路徑才能處理重要的<xref:System.String>輸入。  
  
 下一個最重要的方法是<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。 如果將應用程式轉換為標記表示形式（例如，如果應用程式作為檔保存到 XAML），<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>則負責生成標記表示形式。 在這種情況下，XAML 重要的代碼路徑是傳遞 的`destinationType`<xref:System.String>時。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 和 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 是服務查詢 <xref:System.ComponentModel.TypeConverter> 實作之功能時所使用的支援方法。 您必須實作這些方法來傳回轉換器對等轉換方法所支援類型特有案例的 `true` 。 基於 XAML，這通常表示 <xref:System.String> 類型。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML 的文化特性資訊和類型轉換器  

 每個<xref:System.ComponentModel.TypeConverter>實現都可以對轉換的有效字串的構成內容有自己的解釋，也可以使用或忽略作為參數傳遞的類型描述。 有一個關於文化特性和 XAML 類型轉換的重要考量。 XAML 完全支援使用可當地語系化的字串做為屬性值。 但不支援使用那個可當地語系化的字串做為具有特定文化特性需求的類型轉換器輸入，因為 XAML 屬性值的類型轉換器會使用 `en-US` 文化特性，來包含必然的固定語言剖析行為。 有關此限制的設計原因的詳細資訊，請參閱 XAML 語言規範[\[（MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)）。  
  
 在文化特性可能是問題的範例中，某些文化特性會使用逗號做為數字的小數點分隔符號。 這將與許多 WPF XAML 類型轉換器所具備的行為相衝突，該行為是使用逗號做為分隔符號 (根據歷程的前置參照，例如，常見的 X,Y 格式或逗號分隔清單)。 即使是在局部的 XAML 中傳遞文化特性 (將 `Language` 或 `xml:lang` 設為 `sl-SI` 文化特性，以這種方式使用逗號代表小數點的文化特性範例)，還是無法解決問題。  
  
### <a name="implementing-convertfrom"></a>實作 ConvertFrom  
 若要可做為支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作來重複使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法必須接受字串做為 `value` 參數。 如果字串格式有效，並且可以通過<xref:System.ComponentModel.TypeConverter>實現轉換，則返回的物件必須支援到屬性預期類型的強制轉換。 否則， <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作必須傳回 `null`。  
  
 每個<xref:System.ComponentModel.TypeConverter>實現都可以對轉換的有效字串的構成內容有自己的解釋，也可以使用或忽略作為參數傳遞的類型描述或區域性上下文。 不過，WPF XAML 處理可能不會在所有情況下都將值傳遞至類型描述內容，也可能不會根據 `xml:lang` 來傳遞文化特性。  
  
> [!NOTE]
> 請勿使用大括號字元 (特別是 {)做為字串格式的可能元素。 這些字元保留做為標記延伸序列的進入及結束。  
  
### <a name="implementing-convertto"></a>實作 ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 可能用於序列化支援。 透過自訂類型和其類型轉換器之 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 的序列化支援不是絕對需求。 不過，如果您正在實作控制項，或使用功能某部分的序列化或類別設計，則應該實作 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  
  
 要用作支援 XAML 的<xref:System.ComponentModel.TypeConverter>實現，該轉換器<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>的方法必須接受作為參數支援的類型（或值）的`value`實例。 當`destinationType`參數為 類型<xref:System.String>時，則返回的物件必須能夠強制轉換為<xref:System.String>。 傳回的字串必須代表 `value`的序列化值。 理想情況下，如果該字串傳遞給同一轉換器的<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>實現，則您選擇的序列化格式應該能夠生成相同的值，而不會丟失大量資訊。  
  
 如果該值無法序列化，或者轉換器不支援序列化，則<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>實現必須返回`null`，並且在這種情況下允許引發異常。 但是，如果確實引發異常，則應報告無法將該轉換用作<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>實現的一部分，以便支援<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>首先檢查以避免異常的最佳做法。  
  
 如果`destinationType`參數不是類型<xref:System.String>，您可以選擇自己的轉換器處理。 通常，您將恢復為基本實現處理，這在最基本中<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>會引發特定的異常。  
  
### <a name="implementing-canconvertto"></a>實作 CanConvertTo  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作應該傳回類型 `true` 之 `destinationType` 的 <xref:System.String>，否則會進行基底實作。  
  
### <a name="implementing-canconvertfrom"></a>實作 CanConvertFrom  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 實作應該傳回類型 `true` 之 `sourceType` 的 <xref:System.String>，否則會進行基底實作。  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>套用 TypeConverterAttribute  
 為了使自訂類型轉換器被 XAML 處理器用作自訂類的代理類型轉換器，必須將 應用<xref:System.ComponentModel.TypeConverterAttribute>到類定義。 您透過屬性指定的 <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> 必須是您自訂類型轉換器的類型名稱。 如果已套用這個屬性，當 XAML 處理器處理屬性類型使用您自訂類別類型的值時，就可以輸入字串並傳回物件執行個體。  
  
 您也可以提供每個屬性的類型轉換器。 而不是將 應用於<xref:System.ComponentModel.TypeConverterAttribute>類定義，而是將其應用於屬性定義（主定義，而不是其中的`get`/`set`實現）。 屬性的類型必須符合您自訂類型轉換器所處理的類型。 如果已套用這個屬性，則在 XAML 處理器處理該屬性的值時，可以處理輸入字串，並傳回物件執行個體。 如果選擇使用 Microsoft .NET Framework 或其他庫的屬性類型（其中不能控制類定義且無法應用<xref:System.ComponentModel.TypeConverterAttribute>）。因此，每個屬性類型轉換器技術特別有用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.TypeConverter>
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
