---
title: "WPF XAML 的 XAML 命名空間和命名空間對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件, 將命名空間對應至"
  - "類別, 將命名空間對應至"
  - "自訂類別, 將命名空間對應至"
  - "對應命名空間"
  - "命名空間對應"
  - "命名空間"
  - "XAML, 命名空間對應"
  - "XAML, 命名空間"
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# WPF XAML 的 XAML 命名空間和命名空間對應
本主題將進一步說明時常可在 WPF XAML 檔案的根標記中找到的兩個 XAML 命名空間對應的呈現和用途。  此外，本文也將說明如何使用您自己的程式碼中定義的項目，以及\/或個別組件 \(Assembly\) 內的項目，產生類似的對應。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 何謂 XAML 命名空間？  
 XAML 命名空間其實是 XML 命名空間概念的延伸。  指定 XAML 命名空間的技巧，仍需依賴 XML 命名空間語法、使用 URI 做為命名空間識別項的慣例、使用前置字元來提供參考相同標記來源中之多個命名空間的方式等等。  在 XAML 的 XML 命名空間定義中，最主要加入的一個概念，就是 XAML 命名空間同時宣示了所用標記可保有唯一性的範圍，而且也影響特定 CLR 命名空間和參考組件可能支援標記實體的方式。  後面這項考量也受到 XAML 結構描述內容的概念影響。  但是，若要了解 WPF 搭配 XAML 命名空間運作的方式，您通常可以從下列角度想到 XAML 命名空間：預設 XAML 命名空間、XAML 語言命名空間，以及由您的 XAML 標記直接對應至特定支援 CLR 命名空間與參考組件的任何其他 XAML 命名空間。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## WPF 和 XAML 命名空間宣告  
 在許多 XAML 檔案之根標記中的命名空間宣告內，您通常會看到兩個 XML 命名空間宣告。  第一個宣告會對應整個 WPF 用戶端 \/ 架構 XAML 命名空間做為預設值：  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 第二個宣告對應另一個 XAML 命名空間，而且 \(通常會\) 將它對應到 `x:` 前置字元。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 這些宣告之間的關聯性在於，`x:` 前置字元對應支援的內建 \(Intrinsic\) 屬於 XAML 語言定義的一部分，而 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 則是使用 XAML 做為語言的一項實作，並且會針對 XAML 定義其物件的詞彙。  由於 WPF 詞彙的用途比 XAML 內建的用途更為普遍，因此 WPF 詞彙為預設的對應項目。  
  
 此 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 內的專案範本、範例程式碼和語言功能的文件，都採用 `x:` 前置字元慣例對應 XAML 語言內建支援。  XAML 命名空間定義了許多常用的功能，甚至包括基礎 WPF 應用程式需要的功能。  例如，為了透過部分類別將任何程式碼後置 \(Code\-Behind\) 聯結到 XAML 檔案，您必須在相關 XAML 檔案的根項目中將該類別命名為 `x:Class` 屬性。  或者，若您想存取 XAML 頁面中定義的任何項目做為有索引鍵的資源，則應該在該項目上設定其 `x:Key` 屬性。  如需 XAML 這些方面和其他方面的詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)或 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## 對應至自訂類別和組件  
 您可以使用 `xmlns` 前置字元宣告內的一系列語彙基元 \(Token\)，將 XML 命名空間對應至組件，此方法與標準 WPF 和 XAML 內建 XAML 命名空間對應至前置字元的方式類似。  
  
 此語法接受下列可能的具名語彙基元和下列值：  
  
 `clr-namespace:`組件內宣告的 CLR 命名空間，其中包含要公開為項目的公用型別。  
  
 `assembly=`：包含部分或所有參考之 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間的組件。  此值通常只是組件的名稱，不是路徑，且不包含副檔名 \(例如 .dll 或 .exe\)。  您必須建立該組件的路徑，做為包含您嘗試對應之 XAML 的專案檔中的專案參考。  為了加入版本控制和強式名稱簽章，`assembly` 值也可以是 <xref:System.Reflection.AssemblyName> 所定義的字串，而不是簡單的字串名稱。  
  
 請注意，分隔 `clr-namespace`  語彙基元及其值的字元是冒號 \(:\)，而分隔 `assembly` 語彙基元和其值的字元則是等號 \(\=\)。  這兩個語彙基元之間使用的字元時分號。  同時，不要在宣告中的任何位置包含空白。  
  
### 基本自訂對應範例  
 下列程式碼會定義範例自訂類別：  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 這個自訂類別將接著編譯為程式庫，並且根據專案設定 \(未顯示\) 命名為 `SDKSampleLibrary`。  
  
 為了參考這個自訂類別，您還需要將它加入做為目前專案的參考，通常會使用 Visual Studio 中的方案總管執行這項操作。  
  
 現在，您有包含類別的程式庫，且專案設定中包含該程式庫的參考，因此您可以加入下列前置字元對應做為 XAML 中的根項目：  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 若要全部組合起來，下面的 XAML 包括自訂對應，且根標記中包含一般預設值和 x: 對應，然後會使用具有前置字元的參考執行個體化該 UI 中的 `ExampleClass`：  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### 對應至目前組件  
 如果要在與參考自訂類別的應用程式程式碼相同的組件內定義參考的 `clr-namespace`，可以忽略 `assembly`。  或者，您也可以改用適用於這種情況的對等語法，也就是指定 `assembly=`，但不要在等號後面加上字串語彙基元。  
  
 在相同組件中定義的自訂類別可以當做頁面的根項目。  部分類別不需要對應；如果您想將類別當做 XAML 中的項目加以參考，只需要對應您的應用程式中某個頁面之部分類別以外的其他類別即可。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## 在組件中將 CLR 命名空間對應至 XML 命名空間  
 WPF 會定義一個 CLR 屬性供 XAML 處理器使用，以便將多個 CLR 命名空間對應至單一 XAML 命名空間。  這個屬性 \(即 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>\) 位於產生組件之原始程式碼的組件層級中。  WPF 組件原始程式碼會使用這個屬性將各種不同的通用命名空間 \(例如 <xref:System.Windows> 和 <xref:System.Windows.Controls>\) 對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 接受兩個參數：XML\/XAML 命名空間名稱和 CLR 命名空間名稱。  可能會有多個 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 將多個 CLR 命名空間對應至同一個 XML 命名空間。  對應完成之後，如果需要，您也可以透過在部分類別程式碼後置頁面中提供適當的 `using` 陳述式，以沒有完整限定性條件的方式參考這些命名空間的成員。  如需詳細資訊，請參閱 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>。  
  
## XAML 範本中的設計工具命名空間與其他前置字元  
 如果您正在使用 WPF XAML 的開發環境和 \(或\) 設計工具，您可能會注意到 XAML 標記內有其他已定義的 XAML 命名空間 \/ 前置字元。  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 使用的設計工具命名空間通常會對應至前置字元 `d:`。  適用於 WPF 的較新專案範本可能會預先對應此 XAML 命名空間，以支援 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 和其他設計環境之間交換 XAML。  此設計 XAML 命名空間是用來保存在設計工具中來回往返 XAML 架構 UI 時的設計狀態。  此外，還會用於像 `d:IsDataSource` 這類讓執行階段資料來源得以用在設計工具中的功能。  
  
 其他您可能會看到的已對應前置字元為 `mc:`。  `mc:` 代表標記相容性 \(Markup Compatibility\)，會運用不一定只有 XAML 才適用的標記相容性模式。  在某種程度上，標記相容性功能可用於在架構之間或在其他支援實作界限之間交換 XAML、銜接 XAML 結構描述內容、提供設計工具中有限模式的相容性等等。  如需標記相容性概念和其與 WPF 之關聯性的詳細資訊，請參閱[標記相容性 \(mc:\) 語言功能](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md)。  
  
## WPF 和組件載入  
 WPF 的 XAML 結構描述內容已與 WPF 應用程式模型整合，而後者會使用 CLR 定義的 <xref:System.AppDomain> 概念。  下列步驟說明 XAML 結構描述內容如何根據 WPF 使用的 <xref:System.AppDomain> 和其他因素，解譯在執行階段或設計階段載入組件或尋找型別的方式。  
  
1.  在 <xref:System.AppDomain> 中逐一查看：從最新載入的組件開始，尋找名稱所有層面皆符合的已載入組件。  
  
2.  如果是限定名稱，則在限定名稱上呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
3.  如果限定名稱的簡短名稱 \+ 公開金鑰語彙基元符合當初載入標記的來源組件，則傳回該組件。  
  
4.  使用簡短名稱 \+ 公開金鑰語彙基元來呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
5.  如果是未限定名稱，則呼叫 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>。  
  
 鬆散 XAML 不使用步驟 3，因為沒有載入來源組件。  
  
 WPF 的已編譯 XAML \(透過 XamlBuildTask 產生\) 不使用 <xref:System.AppDomain> 中的已載入組件 \(步驟 1\)。  此外，XamlBuildTask 永遠不應輸出未限定名稱，因此步驟 5 不適用。  
  
 已編譯 BAML \(透過 PresentationBuildTask 產生\) 使用所有步驟，但 BAML 同樣不應該包含未限定組件名稱。  
  
## 請參閱  
 [了解 XML 命名空間](http://go.microsoft.com/fwlink/?LinkId=98069)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)