---
title: .NET XAML 服務的 XAML 命名空間
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071840"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>.NET XAML 服務的 XAML 命名空間
XAML 命名空間是一個擴展 XML 命名空間定義的概念。 與 XML 命名空間類似,可以使用標`xmlns`記中 的屬性定義 XAML 命名空間。 XAML 命名空間也表示在 XAML 節點流和其他 XAML 服務 API 中。 本主題定義了 XAML 命名空間概念,並介紹了如何定義 XAML 命名空間並由 XAML 架構上下文和 .NET XAML 服務的其他方面使用。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML 命名空間與 XAML 命名空間  
 XAML 命名空間是一個專門的 XML 命名空間,就像 XAML 是 XML 的專用形式,並使用基本的 XML 形式進行標記一樣。 在標記中,透過應用於元素`xmlns`的屬性聲明 XAML 命名空間及其映射。 可以`xmlns`對聲明 XAML 命名空間的同一元素進行聲明。 對元素所做的 XAML 命名空間聲明對該元素、該元素的所有屬性以及該元素的所有子級都有效。 屬性可以使用與包含該屬性的元素不相同的 XAML 命名空間,只要屬性名稱本身在標記中引用前置碼作為其屬性名稱的一部分。  
  
 XAML 命名空間與 XML 命名空間的區別是,XML 命名空間可用於引用架構或僅用於區分實體。 對於 XAML,XAML 中使用的類型和成員最終必須解析為支援類型,並且 XML 架構概念不能很好地應用於此功能。 XAML 命名空間包含 XAML 架構上下文必須具有的資訊,以便執行此類型映射。  
  
## <a name="xaml-namespace-components"></a>XAML 命名空間元件  
 XAML 命名空間定義有兩個元件:前置碼和識別碼。 當在標記中聲明 XAML 命名空間或在 XAML 類型系統中定義時,每個元件都存在。  
  
 首碼可以是[XML 1.0 規範中 W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)允許的任何字串。 按照慣例,前置通常是短字串,因為前置字串,因為前置字串,因為前置多次。 某些用於多個 XAML 實現中的 XAML 命名空間使用特定的常規首碼。 例如,XAML 語言 XAML 命名空間通常`x`使用前綴進行映射。 您可以定義預設的 XAML 命名空間,其中前置碼在定義中未給出,但如果by.NET XAML 服務 API 定義或查詢,則表示為空字串。 通常,特意選擇預設 XAML 命名空間,以便 XAML 實現技術及其方案和詞彙量最大限度地省略標記。  
  
 識別碼可以是[XML 1.0 規範中 W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)允許的任何字串。 按照慣例,XML 命名空間或 XAML 命名空間的標識符通常以 URI 形式提供,通常作為協定限定的絕對 URI。 通常,定義特定 XAML 詞彙表的版本資訊作為路徑字串的一部分隱含。 XAML 命名空間添加除 XML URI 約定之外的其他標識符約定。 對於 XAML 命名空間,識別符傳達 XAML 架構上下文所需的資訊,以便解析在 XAML 命名空間下指定為元素的類型,或向成員解析屬性。  
  
 為了將資訊傳達給 XAML 架構上下文,XAML 命名空間的標識符可能仍以 URI 形式。 但是,在這種情況下,URI 也聲明為特定程式集或程式集清單中的匹配標識符。 這是通過在裝配體中分配 程式集來<xref:System.Windows.Markup.XmlnsDefinitionAttribute>實現 的。 在 .NET XAML 服務中,預設的 XAML 架構上下文支援此方法,用於標識 XAML 命名空間和在屬性程式集中支援基於 CLR 的類型解析行為。 更一般情況下,此約定可用於 XAML 架構上下文合併 CLR 或基於預設 XAML 架構上下文的情況,這是從 CLR 程式集讀取 CLR 屬性所必需的。  
  
 XAML 命名空間也可以由通訊 CLR 命名空間和類型定義程式集的約定標識。 此約定用於包含類型的程式集中不存在<xref:System.Windows.Markup.XmlnsDefinitionAttribute>歸因的情況。 此約定可能比URI約定複雜,並且具有歧義和重複的可能性,因為有多種方式引用程式集。  
  
 使用 CLR 命名空間和程式集約定的識別碼的最基本形式如下:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`是`; assembly=`語法的文本元件。  
  
 *clrnsName*是識別 CLR 命名空間的字串名稱。 此字串名稱包括任何內部點字元 (.),這些字元提供有關 CLR 命名空間及其與其他 CLR 命名空間的關係的提示。
  
 *程式集ShortName*是定義 XAML 中有用的類型的程式集的字串名稱。 要透過聲明的 XAML 命名空間存取的類型應由程式集定義,並在*clrnsName*指定的 CLR 命名空間中聲明。 此字串名稱通常與 報告<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>的資訊並行。  
  
 CLR 命名空間和程式集約定的更完整定義如下:  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *程式集名稱*表示<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>作為 輸入合法的任何字串。 此字串可以包括區域性、公鑰或版本資訊(這些概念的定義在<xref:System.Reflection.Assembly>的參考主題中定義。 COFF 格式和證據(如其他過載<xref:System.Reflection.Assembly.Load%2A>使用 )與 XAML 程式集載入目的無關;所有載入資訊必須作為字串顯示。  
  
 為程式集指定公開金鑰是 XAML 安全性的有用技術,或者用於刪除如果程式集以簡單名稱載入或預先存在於快取或應用程式域中可能存在的歧義。 有關詳細資訊,請參閱[XAML 安全注意事項](security-considerations.md)。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML 服務 API 中的 XAML 命名空間聲明  
 在 XAML 服務 API 中,XAML 命名空間聲明<xref:System.Xaml.NamespaceDeclaration>由物件表示。 如果要在代碼中聲明 XAML 命名空間,則<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>調用 建構函數。 與`ns``prefix`參數指定為字串,提供這些參數的輸入對應於本主題中前面提供的 XAML 命名空間識別碼和 XAML 命名空間前置字串的定義。  
  
 如果要作為 XAML 節點流的一部分或通過對 XAML 類型系統的其他訪問來檢查<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType>XAML 命名 空間<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType>資訊,則報告 XAML 命名空間標識符,並報告 XAML 命名空間前綴。  
  
 在 XAML 節點流中,XAML 命名空間資訊可以顯示為 XAML 節點,該節點位於它所應用的實體之前。 這包括 XAML 命名空間資訊在`StartObject`XAML 根元素之前的情況。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md)。  
  
 對於許多使用 .NET XAML 服務 API 的方案,預計至少存在一個 XAML 命名空間聲明,並且聲明必須包含或引用 XAML 架構上下文所需的資訊。 XAML 命名空間必須指定要載入的程式集,或者説明解析命名空間和程式集中已載入或 XAML 架構上下文已知的特定類型。  
  
 為了生成 XAML 節點流,必須透過 XAML 架構上下文提供 XAML 類型資訊。 如果不首先確定要創建的每個節點的相關 XAML 命名空間,則無法確定 XAML 類型資訊。 此時,尚未創建類型實例,但 XAML 架構上下文可能需要從定義程式集和備份類型中尋找資訊。 例如`<Party><PartyFavor/></Party>`,為了處理標記,XAML 架構上下文必須`ContentProperty`能夠確定`Party`的名稱和類型,因此`Party`還`PartyFavor`必須知道和的 XAML 命名空間資訊。 對於預設 XAML 架構上下文,靜態反射報告在節點流中生成 XAML 類型節點所需的許多 XAML 類型系統資訊。  
  
 為了從 XAML 節點流生成物件圖,必須在原始標記中使用的每個 XAML 首碼中存在 XAML 命名空間聲明,並記錄在 XAML 節點流中。 此時,將創建實例,併發生真正的類型映射行為。  
  
 如果需要預填充 XAML 命名空間資訊,在標記中未定義要使用 XAML 架構上下文的 XAML 命名空間的情況下,<xref:System.Xml.XmlParserContext>可以使用的<xref:System.Xml.XmlReader>一種技術是在 中聲明 的 XML 命名空間聲明。 然後,使用<xref:System.Xml.XmlReader>它作為 XAML 讀取器建構函<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>數的輸入,或 。  
  
 在 .NET XAML 服務中與 XAML 命名空間<xref:System.Windows.Markup.XmlnsDefinitionAttribute><xref:System.Windows.Markup.XmlnsPrefixAttribute>處理相關的另外兩個 API 是屬性和 。 這些屬性適用於程式集。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML 架構上下文用於解釋包含URI的任何 XAML 命名空間聲明。 <xref:System.Windows.Markup.XmlnsPrefixAttribute>由發出 XAML 的工具使用,以便可以使用可預測的前置序列化特定的 XAML 命名空間。 有關詳細資訊,請參閱[自訂類型和函式庫的 XAML 相關 CLR 屬性](clr-attributes-with-custom-types-and-libraries.md)。  
  
## <a name="see-also"></a>另請參閱

- [認識 XAML 節點資料流結構和概念](understanding-xaml-node-stream-structures-and-concepts.md)
