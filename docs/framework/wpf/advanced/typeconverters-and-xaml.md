---
title: "TypeConverter 和 XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, TypeConverter"
  - "TypeConverter 類別"
  - "XAML, TypeConverter 類別"
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# TypeConverter 和 XAML
本主題介紹從字串進行型別轉換，做為一般 XAML 語言功能的目的。  在 .NET Framework 中，若 Managed 自訂類別可當做 XAML 屬性 \(Attribute\) 使用方式中的屬性 \(Property\) 值，<xref:System.ComponentModel.TypeConverter> 類別所提供的特定用途即可充當此種自訂類別的實作一部分。  撰寫自訂類別時，如果要將類別的執行個體當做 XAML 的可設定屬性 \(Attribute\) 值使用，您可能必須將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別、撰寫自訂 <xref:System.ComponentModel.TypeConverter> 類別，或同時進行這兩個動作。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 型別轉換概念  
  
### XAML 和字串值  
 在 XAML 檔案中設定屬性 \(Attribute\) 值時，該值的初始型別為純文字字串。  甚至連其他基本型別 \(例如 <xref:System.Double>\) 一開始都是 XAML 處理器的文字字串。  
  
 XAML 處理器需要有兩項資訊才能處理屬性 \(Attribute\) 值。  第一項資訊是所要設定之屬性的實值型別。  定義屬性值且以 XAML 處理的任何字串最終都必須轉換或解析成該型別的值。  如果該值是 XAML 剖析器理解的基本型別，則會嘗試直接轉換字串。  如果值是列舉，則會使用字串來檢查該列舉中的名稱是否與具名常數相符。  而如果值不是剖析器理解的基本型別也不是列舉，則相關型別必須能夠提供型別的執行個體或提供值 \(根據轉換後的字串而定\)。  這項操作是透過指定型別轉換子類別執行。  型別轉換子實際上是 Helper 類別，可針對 XAML 案例以及 .NET 程式碼中的程式碼呼叫提供其他類別的值。  
  
### 在 XAML 中使用現有的型別轉換行為  
 根據您對基礎 XAML 概念的熟悉度而定，您可能已在基本應用程式 XAML 中使用型別轉換行為而不自知。  例如，WPF 會實際定義數百種採用型別 <xref:System.Windows.Point> 之值的屬性。  <xref:System.Windows.Point> 是說明二維座標空間中座標的值，而且僅擁有兩個重要的屬性：<xref:System.Windows.Point.X%2A> 和 <xref:System.Windows.Point.Y%2A>。  當您再 XAML 中指定一個點時，會在您提供的 <xref:System.Windows.Point.X%2A> 和 <xref:System.Windows.Point.Y%2A> 值之間使用分隔符號 \(通常是逗號\) 將這個點指定為字串。  例如：`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`。  
  
 即使是這個簡單的 <xref:System.Windows.Point> 型別以及它在 XAML 中的簡單用法，都涉及型別轉換子。  在此案例中，就是 <xref:System.Windows.PointConverter> 類別。  
  
 在類別層級定義之 <xref:System.Windows.Point> 的型別轉換子可讓採用 <xref:System.Windows.Point> 之所有屬性的標記使用方式更為簡化。  若此處沒有型別轉換子，您就需要下列更複雜的標記，才能得到與上述相同的範例：  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 通常是依據編碼樣式選擇使用型別轉換字串或較複雜的對等語法。  您的 XAML 工具工作流程可能也會影響設定值的方式。  有些 XAML 工具傾向發出最複雜的標記格式，因為對於反覆存取設計工具檢視或本身擁有的序列化機制而言較為容易。  
  
 一般而言，現有的型別轉換子可在 WPF 和 .NET Framework 型別上，透過檢查類別 \(或屬性\) 是否套用 <xref:System.ComponentModel.TypeConverterAttribute> 的方式發現。  基於 XAML 以及其他目的，此屬性會命名支援該型別值之型別轉換子的類別。  
  
### 型別轉換子和標記延伸  
 標記延伸和型別轉換子可填補 XAML 處理器行為和適用案例中的正交角色。  儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性型別轉換行為在標記延伸實作中通常不會遭到檢查。  換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，即不會叫用套用至該字串上特定屬性或屬性值型別的型別轉換行為。一般來說，標記延伸的目的是在未涉及任何型別轉換子的情況下處理字串及傳回物件。  
  
 需要使用標記延伸 \(而非型別轉換子\) 的其中一種常見的情況是建立已經存在之物件的參考。  最佳的情況是，無狀態的型別轉換子只會產生可能不需要用到的新執行個體。  如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
### 原生型別轉換子  
 在 XAML 剖析器的 WPF 和 .NET Framework 實作中，特定型別會有原生型別轉換處理，但不是習慣上視為基本型別的型別。  這類型別的範例為 <xref:System.DateTime>。  這種情況是根據 .NET Framework 架構運作的方式而定：型別 <xref:System.DateTime> 是在 mscorlib 中定義，但大部分基本程式庫是在 .NET 中定義。  <xref:System.DateTime> 不允許以來自引入相依性 \(<xref:System.ComponentModel.TypeConverterAttribute> 來自 System\) 的另一個組件之屬性設為其屬性，因此不支援透過設定屬性的常用型別轉換探索機制。  而 XAML 剖析器擁有需要這類原生處理的型別清單，並且會以類似於真正處理基本型別的方式處理這些型別  \(在這裡的 <xref:System.DateTime>，則包含對於 <xref:System.DateTime.Parse%2A> 的呼叫\)。  
  
<a name="Implementing_a_Type_Converter"></a>   
## 實作型別轉換子  
  
### TypeConverter  
 前一個 <xref:System.Windows.Point> 範例中有提到 <xref:System.Windows.PointConverter> 類別。  若為 XAML 的 .NET 實作，用於 XAML 的所有型別轉換子都是衍生自基底類別 <xref:System.ComponentModel.TypeConverter> 的類別。  <xref:System.ComponentModel.TypeConverter> 類別存在比 XAML 更早出現的 .NET Framework 版本中；其中一種原始使用方式是為視覺化設計工具中的屬性對話方塊提供字串轉換。  對於 XAML 而言，<xref:System.ComponentModel.TypeConverter> 的角色已延伸，包括做為轉換成字串和從字串轉換的基底類別，提供剖析字串屬性 \(Attribute\) 值的功能，以及將特殊物件屬性 \(Property\) 執行階段值處理為原本的字串，以便序列化為屬性 \(Attribute\)。  
  
 <xref:System.ComponentModel.TypeConverter> 會定義四個與字串轉換有關的成員，以供 XAML 處理目的之用：  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 其中，最重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>。  這個方法會將輸入字串轉換成必要的物件型別。  嚴格說來，可以透過實作 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法，將更廣泛的型別轉換成轉換子希望的目標型別，因此適用於超出 XAML 的目的，例如支援執行階段轉換，不過對於 XAML 的目的而言，這個方法就是去設定處理重要 <xref:System.String> 型別輸入值的轉換型別程式碼路徑。  
  
 第二重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  如果應用程式已轉換成標記表示 \(例如，儲存至 XAML 做為檔案\)，則 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 會負責產生標記表示。  在此情況下，XAML 需要的是您要去設定轉換 <xref:System.String> 型別為 `destinationType` 方法的程式碼路徑。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 和 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 則是在服務查詢 <xref:System.ComponentModel.TypeConverter> 實作的功能時所使用的支援方法。  您必須實作這些方法，針對轉換子的對等轉換方法支援的特定型別案例傳回 `true`。  針對 XAML 的目的，通常這是指 <xref:System.String> 型別。  
  
### XAML 的文化特性資訊和型別轉換子  
 每個 <xref:System.ComponentModel.TypeConverter> 實作對於有效字串的組成可以有各自的詮譯，而且也可以使用或忽略當做參數傳遞的型別描述。  關於文化特性和 XAML 型別轉換有一項重要考量。  XAML 完全支援使用可當地語系化的字串做為屬性值。  但是在特定文化特性需求下，並不支援使用這個可當地語系化的字串做為型別轉換子輸入，因為 XAML 屬性值的型別轉換子涉及必須固定的語言剖析行為，而該行為使用 `en-US` 文化特性。  如需這項限制之設計理由的詳細資訊，請查閱 XAML 語言規格 \([\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\)\)。  
  
 在文化特性可能發生問題的範例中，某些文化特性會使用逗號做為數字的小數點分隔符號。  這種方式會與許多 WPF XAML 型別轉換子的行為發生衝突，因為後者是使用逗號做為分隔符號 \(根據慣用前例，如常用的 X,Y 格式或逗號分隔清單\)。  即使在週邊 XAML \(將 `Language` 或 `xml:lang` 設為 `sl-SI` 文化特性，以此方式使用逗號做為小數點的文化特性範例\) 中傳遞文化特性也無法解決此問題。  
  
### 實作 ConvertFrom  
 為了要當做支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作使用，該轉換子的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法必須接受以字串做為 `value` 參數。  如果字串的格式有效，而且可以透過 <xref:System.ComponentModel.TypeConverter> 實作進行轉換，則傳回的物件必須支援轉型為屬性 \(Property\) 所預期的型別。  否則，<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作就必須傳回 `null`。  
  
 每個 <xref:System.ComponentModel.TypeConverter> 實作對於有效字串的組成可以有各自的詮譯，而且也可以使用或忽略當做參數傳遞的型別描述或文化特性內容。  不過，在 WPF 中的 XAML 語句處理可能不會在所有情況中都傳遞值給型別描述內容，也可能不會根據 `xml:lang` 傳遞文化特性。  
  
> [!NOTE]
>  請勿使用大括弧字元做為字串格式的可能項目，尤其是 {。  這些字元是進入及結束標記延伸序列的保留字元。  
  
### 實作 ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 可能用於序列化支援。  透過自訂型別及其型別轉換子之 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 的序列化支援並不是絕對必要的一項需求。  不過，如果您要實作控制項，或是使用序列化做為類別功能或設計的一部分，則應該實作 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  
  
 為了要當做支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作使用，該轉換子的 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 方法必須接受支援型別的執行個體 \(或值\) 做為 `value` 參數。  若 `destinationType` 參數的型別是 <xref:System.String>，則傳回的物件必須能夠轉型為 <xref:System.String>。  傳回的字串必須代表 `value` 的序列化值。  理想狀況下，如果該字串已傳遞至同一個轉換子的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作，則您選擇的序列化格式應該能夠產生相同的值，以免造成資訊的重大流失。  
  
 如果值無法序列化，或是轉換子不支援序列化，<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 實作必須傳回 `null`，而且可以在這種情況下擲回例外狀況 \(Exception\)。  不過，如果您確實擲回例外狀況，則應回報無法使用該轉換做為 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作一部分的情況，如此才能支援先檢查 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 以避免例外狀況的最佳做法。  
  
 如果 `destinationType` 參數的型別不是 <xref:System.String>，您可以選擇自己的轉換子處理。  通常您會還原成基底實作處理，以便在最基本的 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 中引發特定例外狀況。  
  
### 實作 CanConvertTo  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作應該針對型別 <xref:System.String> 的 `destinationType` 傳回 `true`，否則便會交由基底實作處理。  
  
### 實作 CanConvertFrom  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 實作應該針對型別 <xref:System.String> 的 `sourceType` 傳回 `true`，否則便會交由基底實作處理。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## 套用 TypeConverterAttribute  
 為了讓 XAML 處理器將自訂型別轉換子當做自訂類別的作用型別轉換子使用，您必須將 [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] \(Attribute\) <xref:System.ComponentModel.TypeConverterAttribute> 套用到類別定義。  您透過屬性 \(Attribute\) 指定的 <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> 必須是自訂型別轉換子的型別名稱。  套用此屬性 \(Attribute\) 之後，當 XAML 處理器處理值時，若屬性 \(Property\) 型別使用您的自訂類別型別，該處理器便可輸入字串並傳回物件執行個體。  
  
 您也可以針對個別的屬性提供型別轉換子。  請將 [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> 套用到屬性 \(Property\) 定義 \(主要定義，不是主要定義內的 `get`\/`set` 實作\)，而不要套用到類別定義。  屬性的型別必須符合自訂型別轉換子所處理的型別。  套用此屬性 \(Attribute\) 之後，XAML 處理器就可以在處理該屬性 \(Property\) 的值時，處理輸入字串並傳回物件執行個體。  如果您選擇使用來自 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] 或其他程式庫的屬性型別，而無法控制類別定義，也無法套用 <xref:System.ComponentModel.TypeConverterAttribute>，則根據個別屬性提供型別轉換子的方法特別有用。  
  
## 請參閱  
 <xref:System.ComponentModel.TypeConverter>   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)