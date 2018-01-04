---
title: "TypeConverter 和 XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b7ee4b3b00a675cfafc884d41079b76656bdf49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="typeconverters-and-xaml"></a>TypeConverter 和 XAML
本主題介紹將字串的類型轉換當成一般 XAML 語言功能的目的。 在.NET Framework 中，<xref:System.ComponentModel.TypeConverter>類別將某特定用途做可用來當作 XAML 屬性使用方式中的屬性值的受管理的自訂類別實作的一部分。 如果您撰寫自訂的類別，而且您想要您的類別可做為 XAML 可設定屬性值的執行個體，您可能需要套用<xref:System.ComponentModel.TypeConverterAttribute>至類別，撰寫自訂<xref:System.ComponentModel.TypeConverter>類別，或兩者。  
  

  
## <a name="type-conversion-concepts"></a>類型轉換概念  
  
### <a name="xaml-and-string-values"></a>XAML 和字串值  
 在 XAML 檔案中設定屬性值時，該值的初始類型是純文字的字串。 甚至，其他基本類型，例如<xref:System.Double>一開始是 XAML 處理器的文字字串。  
  
 XAML 處理器需要兩項資訊才能處理屬性值。 第一項資訊是正在設定之屬性的實值類型。 任何定義屬性值並在 XAML 中處理的字串最後必須轉換或解析成該類型的值。 如果值是 XAML 剖析器可理解的基本類型 (例如數值)，則會嘗試直接轉換字串。 如果值是一個列舉，則用來檢查名稱的字串會符合該列舉中的具名常數。 如果值不是剖析器所辨識的基本類型，也不是列舉，則上述類型必須能夠根據已轉換的字串提供類型的執行個體或值。 您可以藉由指定類型轉換器類別來完成此動作。 類型轉換子實際上是一個 Helper 類別，可用於提供另一個類別的值，這兩者均適用於 XAML 案例，可能也適用於利用 .NET 程式碼進行程式碼呼叫。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>在 XAML 中使用現有的類型轉換行為  
 根據您對基礎 XAML 概念的熟悉程度而定，您可能已經在基本應用程式 XAML 中使用類型轉換行為而不自知。 例如，WPF 定義數百個接受類型值的屬性， <xref:System.Windows.Point>。 A<xref:System.Windows.Point>是描述在二維座標空間中的座標值，而且它其實只是有兩個重要的屬性：<xref:System.Windows.Point.X%2A>和<xref:System.Windows.Point.Y%2A>。 當您在 XAML 中指定的點時，您指定它做為字串，以分隔符號 （通常是逗號） 之間<xref:System.Windows.Point.X%2A>和<xref:System.Windows.Point.Y%2A>您提供的值。 例如：`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`。  
  
 即使此簡單類型的<xref:System.Windows.Point>，而且其簡單的使用方式，在 XAML 中包含的型別轉換子。 在此情況下，是類別<xref:System.Windows.PointConverter>。  
  
 類型轉換器<xref:System.Windows.Point>定義在類別層級變異採取的所有屬性的標記使用方式<xref:System.Windows.Point>。 若未在此處使用類型轉換器，您就需要針對先前所示的同一個範例使用下列更多較為詳細的標記：  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 是否要使用類型轉換字串或較為詳細的對等語法，通常是編碼樣式的選擇。 您的 XAML 工具工作流程可能也會影響值的設定方式。 一些 XAML 工具傾向於發出最詳細格式的標記，因為較容易反覆存取設計工具檢視或它自己的序列化機制。  
  
 現有的類型轉換器通常可在 WPF 和.NET Framework 型別上探索藉由檢查類別 （或屬性） 是否有套用<xref:System.ComponentModel.TypeConverterAttribute>。 這個屬性將基於 XAML 用途以及其他可能的用途，針對該類型的值，為支援類型轉換器的類別命名。  
  
### <a name="type-converters-and-markup-extensions"></a>類型轉換器和標記延伸  
 標記延伸和類型轉換器會根據 XAML 處理器行為和套用它們的案例來填滿正交角色。 儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性類型轉換行為在標記延伸實作中通常不會遭到檢查。 換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，也不會在該字串上叫用套用至特定屬性或屬性值類型的類型轉換行為。一般來說，標記延伸的目的是在未涉及任何類型轉換器的情況下，處理字串並傳回物件。  
  
 需要標記延伸而不是類型轉換器的一個常見情況是參考現有的物件。 無狀態類型轉換器充其量只能產生新的執行個體，但這可能不是令人滿意的情況。 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
### <a name="native-type-converters"></a>原生類型轉換器  
 在 XAML 剖析器中的 WPF 和 .NET Framework 實作中，有些特定類型具有原生類型轉換處理，但卻不是依慣例會被視為基本類型的類型。 這類類型的範例是 <xref:System.DateTime>。 這根據.NET Framework 架構的運作方式： 類型<xref:System.DateTime>定義於 mscorlib，在.NET 中的最基本程式庫。 <xref:System.DateTime>不允許使用來自另一個引進相依性的組件的屬性 (<xref:System.ComponentModel.TypeConverterAttribute>來自系統) 因此無法支援所進行的一般類型轉換器探索機制。 而是 XAML 剖析器會有一份需要這類原生處理的類型清單，這些類型的處理方式會與真正基本類型的處理方式類似 (如果是<xref:System.DateTime>這項作業包括呼叫<xref:System.DateTime.Parse%2A>。)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>實作類型轉換器  
  
### <a name="typeconverter"></a>TypeConverter  
 在<xref:System.Windows.Point>先前指定的類別範例<xref:System.Windows.PointConverter>所提到的。 針對.NET 實作的 XAML，會用於 XAML 用途的所有類型轉換器都是衍生自基底類別的<xref:System.ComponentModel.TypeConverter>。 <xref:System.ComponentModel.TypeConverter>類別存在於之前的 XAML 存在.NET Framework 版本中，則為其原始的使用方式的其中一個就是提供視覺化設計工具中的屬性對話方塊的字串轉換。 針對 XAML，所扮演的角色<xref:System.ComponentModel.TypeConverter>已擴展成包含正在剖析字串的屬性值，可能處理特定物件屬性的執行階段值的字串到啟用的目標字串和從字串轉換的基底類別序列化為屬性。  
  
 <xref:System.ComponentModel.TypeConverter>定義四個成員與相關的轉換與基於 XAML 處理字串：  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 其中，最重要的方法是<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>。 這個方法會將輸入字串轉換為所需的物件類型。 嚴格來說，<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>方法可能會實作更廣泛的型別轉換為轉換器的預定的目的地類型，並將因此提供不僅 XAML，例如支援執行階段轉換，但基於 XAML 的用途它是只可以處理的程式碼路徑<xref:System.String>很重要的輸入。  
  
 下一個最重要的方法是<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。 （例如，如果它儲存為 XAML 檔案），如果要應用程式轉換成標記呈現，<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>會負責產生標記呈現。 在此情況下，XAML 的重要程式碼路徑時，您將傳遞`destinationType`的<xref:System.String>。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 和 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 是服務查詢 <xref:System.ComponentModel.TypeConverter> 實作之功能時所使用的支援方法。 您必須實作這些方法來傳回轉換器對等轉換方法所支援類型特有案例的 `true` 。 基於 XAML，這通常表示 <xref:System.String> 類型。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML 的文化特性資訊和類型轉換器  
 每個<xref:System.ComponentModel.TypeConverter>實作可以有它自己的解譯什麼可替代轉換的有效字串的也可以使用或忽略傳遞為參數的類型描述。 有一個關於文化特性和 XAML 類型轉換的重要考量。 XAML 完全支援使用可當地語系化的字串做為屬性值。 但不支援使用那個可當地語系化的字串做為具有特定文化特性需求的類型轉換器輸入，因為 XAML 屬性值的類型轉換器會使用 `en-US` 文化特性，來包含必然的固定語言剖析行為。 如需這項限制之設計考量的詳細資訊，請參閱 XAML 語言規格 ([\[MS-XAML\] (英文)](http://go.microsoft.com/fwlink/?LinkId=114525))。  
  
 在文化特性可能是問題的範例中，某些文化特性會使用逗號做為數字的小數點分隔符號。 這將與許多 WPF XAML 類型轉換器所具備的行為相衝突，該行為是使用逗號做為分隔符號 (根據歷程的前置參照，例如，常見的 X,Y 格式或逗號分隔清單)。 即使是在局部的 XAML 中傳遞文化特性 (將 `Language` 或 `xml:lang` 設為 `sl-SI` 文化特性，以這種方式使用逗號代表小數點的文化特性範例)，還是無法解決問題。  
  
### <a name="implementing-convertfrom"></a>實作 ConvertFrom  
 若要可做為支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作來重複使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法必須接受字串做為 `value` 參數。 如果字串處於有效格式，並且可以將轉換<xref:System.ComponentModel.TypeConverter>實作中，則傳回的物件必須支援轉型至屬性所預期的類型。 否則， <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作必須傳回 `null`。  
  
 每個<xref:System.ComponentModel.TypeConverter>實作可以有它自己的解譯什麼可替代轉換的有效字串的也可以使用或忽略傳遞為參數的類型描述或文化特性內容。 不過，WPF XAML 處理可能不會在所有情況下都將值傳遞至類型描述內容，也可能不會根據 `xml:lang` 來傳遞文化特性。  
  
> [!NOTE]
>  請勿使用大括號字元 (特別是 {)做為字串格式的可能元素。 這些字元保留做為標記延伸序列的進入及結束。  
  
### <a name="implementing-convertto"></a>實作 ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 可能用於序列化支援。 透過自訂類型和其類型轉換器之 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 的序列化支援不是絕對需求。 不過，如果您正在實作控制項，或使用功能某部分的序列化或類別設計，則應該實作 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  
  
 為了能夠當做<xref:System.ComponentModel.TypeConverter>支援 XAML 中，實作<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>該轉換器的方法必須接受型別 （或值） 所支援的執行個體為`value`參數。 當`destinationType`參數是型別<xref:System.String>，則傳回的物件必須可以轉型為<xref:System.String>。 傳回的字串必須代表 `value` 的序列化值。 在理想情況下，您所選擇的序列化格式應該是能夠產生相同的值，如果該字串傳遞到<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>實作相同的轉換子，而不會明顯遺失資訊。  
  
 如果無法序列化值，或轉換器不支援序列化，<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>實作必須傳回`null`，以及允許在此情況下擲回例外狀況。 如果您確實擲回例外狀況，則應該報告無法使用該轉換的一部分，但您<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>實作以便最佳作法來檢查是否有<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>第一次支援以避免例外狀況。  
  
 如果`destinationType`參數的類型不是<xref:System.String>，您可以選擇專屬轉換器處理。 一般而言，您會回復成基底實作處理，而在 basemost<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>引發特定例外狀況。  
  
### <a name="implementing-canconvertto"></a>實作 CanConvertTo  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作應該傳回類型 `true` 之 `destinationType` 的 <xref:System.String>，否則會進行基底實作。  
  
### <a name="implementing-canconvertfrom"></a>實作 CanConvertFrom  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 實作應該傳回類型 <xref:System.String> 之 `sourceType` 的 `true`，否則會進行基底實作。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>套用 TypeConverterAttribute  
 為了讓您自訂類型轉換器，以用做自訂類別，在 XAML 處理器的類型轉換器，您必須先套用[!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)]<xref:System.ComponentModel.TypeConverterAttribute>至類別定義。 您透過屬性指定的 <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> 必須是您自訂類型轉換器的類型名稱。 如果已套用這個屬性，當 XAML 處理器處理屬性類型使用您自訂類別類型的值時，就可以輸入字串並傳回物件執行個體。  
  
 您也可以提供每個屬性的類型轉換器。 而不是套用[!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)]<xref:System.ComponentModel.TypeConverterAttribute>類別定義中，以將它套用至屬性定義 (主要定義，不`get` / `set`內實作)。 屬性的類型必須符合您自訂類型轉換器所處理的類型。 如果已套用這個屬性，在 XAML 處理器處理該屬性的值時，就可以處理輸入字串並傳回物件執行個體。 如果您選擇使用的屬性類型來自 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] 或無法控制類別定義而且無法在該處套用 <xref:System.ComponentModel.TypeConverterAttribute> 的某個其他程式庫，則每個屬性的類型轉換器技術特別有用。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ComponentModel.TypeConverter>  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
