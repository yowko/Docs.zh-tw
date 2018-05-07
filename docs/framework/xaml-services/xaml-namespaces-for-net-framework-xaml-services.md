---
title: .NET Framework XAML 服務的 XAML 命名空間
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 842cfb31e21c59bb886ccd266d19c40c64557519
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML 服務的 XAML 命名空間
XAML 命名空間是擴充的 XML 命名空間定義的概念。 類似的 XML 命名空間，您可以定義 XAML 命名空間使用`xmlns`標記中的屬性。 XAML 命名空間也都是在 XAML 節點資料流和其他 XAML 服務應用程式開發介面中表示。 本主題會定義 XAML 命名空間概念，並說明如何 XAML 命名空間可定義和 XAML 結構描述內容和其他方面的.NET Framework XAML 服務所使用。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML 命名空間和 XAML 命名空間  
 XAML 命名空間是特製化的 XML 命名空間，就如同 XAML 是一種特殊的形式的 XML，並使用其標記基本的 XML 格式。 在標記中，宣告 XAML 命名空間和其對應到`xmlns`屬性套用至項目。 `xmlns`中宣告 XAML 命名空間的相同項目進行宣告。 XAML 命名空間宣告，對項目是有效的項目，該項目的所有屬性和項目的所有子系。 屬性可以使用 XAML 命名空間不包含屬性的項目相同，只要本身的屬性名稱會參考前置詞做為其在標記中的屬性名稱的一部分。  
  
 XAML 命名空間與 XML 命名空間不同的是 XML 命名空間可能會用來參考結構描述，或可能用來直接區分實體。 針對 XAML，型別和成員在 XAML 中使用必須最終會解析為備份類型，而 XML 結構描述的概念並不適用於這項功能。 XAML 命名空間包含的 XAML 結構描述內容必須具有可用性，以執行此類型對應的資訊。  
  
## <a name="xaml-namespace-components"></a>XAML 命名空間元件  
 XAML 命名空間定義具有兩個元件： 前置詞和識別項。 每個元件會在標記中，宣告或定義 XAML 類型系統中的 XAML 命名空間時。  
  
 允許的前置詞可以是任何字串[W3C Namespaces in XML 1.0 規格](http://go.microsoft.com/fwlink/?LinkID=161735)。 依照慣例的前置詞是通常很短的字串，因為前置詞的一般標記檔案中重複多次。 適用於多個 XAML 實作中特定 XAML 命名空間使用特定的傳統前置詞。 例如，在 XAML 語言 XAML 命名空間通常對應使用前置詞`x`。 您可以定義預設 XAML 命名空間前置詞中定義未指定，但如果定義或查詢 by.NET Framework XAML 服務應用程式開發介面，以空字串。 一般來說，預設 XAML 命名空間刻意選擇才能升級而發揮最大的數量的前置詞省略標記的 XAML 實作的技術和案例和詞彙。  
  
 允許的範圍，此識別碼可以是任何字串[W3C Namespaces in XML 1.0 規格](http://go.microsoft.com/fwlink/?LinkID=161735)。 依照慣例，識別項的 XML 命名空間或 XAML 命名空間通常可以在 URI 形式中，通常是通訊協定合格的絕對 URI。 通常，定義特定的 XAML 詞彙的版本資訊會隱含的路徑字串的一部分。 XAML 命名空間將新增的 XML URI 慣例之外的其他識別項慣例。 針對 XAML 命名空間識別項通訊以解析類型指定為該 XAML 命名空間下的項目，或解析成員屬性，會將 XAML 結構描述內容所需的資訊。  
  
 為了傳達 XAML 結構描述內容的資訊，XAML 命名空間的識別項可能仍然是 URI 形式。 不過，在此情況下 URI 也宣告為特定組件或組件清單中的比對識別項。 這由組件中設定其屬性的組件<xref:System.Windows.Markup.XmlnsDefinitionAttribute>。 預設 XAML 結構描述內容在.NET Framework XAML 服務中支援這個方法，找出 XAML 命名空間，並支援屬性化組件中的 CLR 型別解析行為。 較常見地，這個慣例可用的 XAML 結構描述內容，結合在 CLR 或會需要從 CLR 組件讀取 CLR 屬性的預設 XAML 結構描述內容為基礎的狀況。  
  
 XAML 命名空間也可以識別的 CLR 命名空間和類型定義的組件進行通訊的慣例。 這個慣例用於情況下，未<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性存在於包含類型的組件。 這個慣例比 URI 慣例可能更為複雜，而且也有可能會模稜兩可和重複作業，因為有多個方法的參考組件。  
  
 使用 CLR 命名空間和組件慣例的識別項最基本的形式如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` 和`; assembly=`語法的常值的元件。  
  
 *clrnsName*已識別的 CLR 命名空間的字串名稱。 此字串名稱包括提供有關 CLR 命名空間和其關聯到其他的 CLR 命名空間提示任何內部點字元 （.）。  
  
 *assemblyShortName*字串名稱的組件所定義，可用於 XAML 的類型。 預期要透過宣告 XAML 命名空間的類型定義的組件，以及特別是在所指定的 CLR 命名空間中宣告*clrnsName*。 此字串名稱通常與資訊所報告<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>。  
  
 CLR 命名空間和組件規範的更完整的定義如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName*表示是做為合法的任何字串<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>輸入。 這個字串可以包含文化特性、 公開金鑰或版本資訊 (這些概念的定義是中的參考主題<xref:System.Reflection.Assembly>)。 COFF 格式和辨識項 (所使用的其他多載的<xref:System.Reflection.Assembly.Load%2A>) 不相關的 XAML 組件載入之用，所有的載入資訊必須以字串呈現。  
  
 指定組件的公開金鑰是為 XAML 安全性，或移除可能模稜兩可，如果組件載入的簡單名稱，或預先存在的快取或應用程式網域中可以存在一個實用的方法。 如需詳細資訊，請參閱[XAML 安全性考量](../../../docs/framework/xaml-services/xaml-security-considerations.md)。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>在 XAML 服務應用程式開發介面的 XAML 命名空間宣告  
 在 XAML 服務應用程式開發介面，XAML 命名空間宣告由<xref:System.Xaml.NamespaceDeclaration>物件。 如果您宣告在程式碼中的 XAML 命名空間，您呼叫<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>建構函式。 `ns`和`prefix`參數會指定為字串，並提供這些參數的輸入對應至 XAML 命名空間識別項和 XAML 命名空間前置詞的定義，如本主題先前所提供。  
  
 如果您正在檢查 XAML 節點資料流的一部分或透過其他存取 XAML 類型系統中，XAML 命名空間資訊<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType>會報告 XAML 命名空間識別項和<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType>會報告 XAML 命名空間前置詞。  
  
 在 XAML 節點資料流，XAML 命名空間資訊可以顯示為 XAML 節點之前它所套用的實體。 這包括情況下，XAML 命名空間資訊位於何處`StartObject`的 XAML 根項目。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
 使用.NET Framework XAML 服務 API 的許多案例，至少一個 XAML 命名空間宣告必須要有，，和宣告必須是包含或參考的 XAML 結構描述內容所需的資訊。 XAML 命名空間必須指定要載入，或協助解決命名空間和組件已載入或已知的 XAML 結構描述內容內的特定類型的組件。  
  
 若要產生 XAML 節點資料流，XAML 型別資訊必須可用，透過 XAML 結構描述內容。 無法判斷 XAML 型別資訊，而不先決定要建立每個節點的相關 XAML 命名空間。 此時，棒的是，建立任何類型的執行個體，但可能需要 XAML 結構描述內容查詢從定義組件和備份類型的資訊。 例如，若要處理的標記`<Party><PartyFavor/></Party>`，XAML 結構描述內容必須能夠判斷名稱和型別`ContentProperty`的`Party`，因此也必須知道的 XAML 命名空間資訊和`Party`和`PartyFavor`。 如果預設 XAML 結構描述內容，是靜態反映報告大部分需要在節點資料流中產生 XAML 型別節點的 XAML 類型系統資訊。  
  
 以產生物件圖形中 XAML 節點資料流，XAML 命名空間宣告必須存在於每個 XAML 前置詞用於原始的標記，而且記錄在 XAML 節點資料流。 此時，會建立執行個體，並就會發生，則為 true 的型別對應行為。  
  
 如果您要預先填入的情況下，未在標記中，定義您想要使用的 XAML 結構描述內容的 XAML 命名空間中的 XAML 命名空間資訊可以使用其中一種技術是宣告中的 XML 命名空間宣告<xref:System.Xml.XmlParserContext>如<xref:System.Xml.XmlReader>. 然後使用該<xref:System.Xml.XmlReader>做為輸入的 XAML 讀取器建構函式或<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>。  
  
 屬性是與相關的.NET Framework XAML 服務中處理的 XAML 命名空間的其他兩個 API<xref:System.Windows.Markup.XmlnsDefinitionAttribute>和<xref:System.Windows.Markup.XmlnsPrefixAttribute>。 這些屬性套用至組件。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 可由 XAML 結構描述內容來解譯包含 URI 的任何 XAML 命名空間宣告。 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 用來發出，讓特定的 XAML 命名空間具有可預測的前置詞可序列化的 XAML 工具。 如需詳細資訊，請參閱[XAML-Related CLR 屬性之自訂類型和程式庫](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="see-also"></a>另請參閱  
 [認識 XAML 節點資料流結構和概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
