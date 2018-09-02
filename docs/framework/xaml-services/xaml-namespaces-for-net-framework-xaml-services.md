---
title: .NET Framework XAML 服務的 XAML 命名空間
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: ac6554cbdeb5bc6e0fe7fb96ea95d0143c293d22
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403215"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML 服務的 XAML 命名空間
XAML 命名空間是一個擴充的 XML 命名空間定義的概念。 類似於 XML 命名空間，您可以定義 XAML 命名空間使用`xmlns`標記中的屬性。 XAML 命名空間也都被表示 XAML 節點資料流和其他 XAML 服務 Api。 本主題定義 XAML 命名空間概念，並描述如何定義 XAML 命名空間，並可供 XAML 結構描述內容與.NET Framework XAML 服務的其他層面。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML 命名空間和 XAML 命名空間  
 XAML 命名空間是特製化的 XML 命名空間，就如同 XAML 是一種特殊的形式的 XML，並使用其標記的基本的 XML 格式。 在標記中，您宣告 XAML 命名空間和其對應到`xmlns`屬性套用至項目。 `xmlns`宣告可以對相同的 XAML 命名空間中宣告的項目。 無效的項目，該項目的所有屬性和項目的所有子系的 XAML 命名空間宣告，對項目。 屬性可以使用 XAML 命名空間不包含屬性的項目相同，只要本身的屬性名稱會參考前置詞，其在標記中的屬性名稱的一部分。  
  
 XAML 命名空間與 XML 命名空間不同的是 XML 命名空間可能會用來參考結構描述，或可能會用來只區分實體。 XAML，如的類型和成員，因為 XAML 中使用必須最終會解析支援型別，而 XML 結構描述的概念並不適用於這項功能。 XAML 命名空間包含的 XAML 結構描述內容必須可用於執行此類型對應的資訊。  
  
## <a name="xaml-namespace-components"></a>XAML 命名空間元件  
 XAML 命名空間定義具有兩個元件： 前置詞和識別項。 每個元件都存在時的 XAML 命名空間宣告在標記中，或在 XAML 類型系統中定義。  
  
 允許的首碼可以是任何字串[W3C Namespaces in XML 1.0 規格](https://go.microsoft.com/fwlink/?LinkID=161735)。 依照慣例的前置詞是通常很短的字串，因為前置詞典型的標記檔案中重複許多次。 要在多個 XAML 實作中使用特定 XAML 命名空間使用特定慣例的前置詞。 比方說，XAML 語言 XAML 命名空間通常會對應使用前置詞`x`。 您可以定義預設 XAML 命名空間，前置詞的定義中未指定，但如果定義，或查詢 by.NET Framework XAML 服務 API，以空字串。 一般而言，預設 XAML 命名空間慎重選擇才能升級的前置詞省略最大化的量標記的 XAML 實作的技術和案例和詞彙。  
  
 允許的識別項可以是任何字串[W3C Namespaces in XML 1.0 規格](https://go.microsoft.com/fwlink/?LinkID=161735)。 依照慣例，XML 命名空間或 XAML 命名空間的識別項通常提供 URI 形式，通常是通訊協定限定的絕對 URI。 通常，定義特定的 XAML 詞彙的版本資訊被隱含的路徑字串的一部分。 XAML 命名空間加入 XML URI 慣例之外的其他識別項慣例。 針對 XAML 命名空間識別項進行通訊以解析類型指定為該 XAML 命名空間下的項目，或解析成員屬性，會將 XAML 結構描述內容所需的資訊。  
  
 通訊的 XAML 結構描述內容資訊的用途，XAML 命名空間的識別項可能仍然可以 URI 形式。 不過，在此情況下 URI 同樣宣告為特定組件或組件的清單中的比對識別項。 這由組件中設定其屬性與組件<xref:System.Windows.Markup.XmlnsDefinitionAttribute>。 這個方法，找出的 XAML 命名空間，並支援屬性化組件中的 CLR 型別解析行為受到.NET Framework XAML 服務中的預設 XAML 結構描述內容。 一般來說，這個慣例可以用於 XAML 結構描述內容包含 CLR 或才能讀取來自 CLR 組件的 CLR 屬性的預設 XAML 結構描述內容為基礎的情況。  
  
 XAML 命名空間也可以是所識別的慣例，會與 CLR 命名空間以及型別定義的組件。 這個慣例會用在情況下，未<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性存在於包含類型的組件。 這個慣例可能比 URI 慣例更為複雜，並也可能會發生模稜兩可和重複資料刪除，因為有多種方式來參考組件。  
  
 使用 CLR 命名空間和組件慣例的識別項最基本的形式如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` 和`; assembly=`是常值語法的元件。  
  
 *clrnsName*是識別 CLR 命名空間的字串名稱。 此字串名稱包含任何內部的點字元 （.），提供有關 CLR 命名空間和其他的 CLR 命名空間的關聯性的提示。  
  
 *assemblyShortName*是定義在 XAML 中有用的類型的組件的字串名稱。 透過宣告 XAML 命名空間存取類型的組件所定義，以及特別是宣告所指定的 CLR 命名空間內預期*clrnsName*。 此字串名稱通常平行資訊所回報<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>。  
  
 更完整的 CLR 命名空間和組件慣例的定義如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *組件名稱*  
  
 *assemblyName*表示任何字串做為合法<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>輸入。 這個字串可以包含文化特性、 公開金鑰或版本資訊 (這些概念的定義中的參考主題定義<xref:System.Reflection.Assembly>)。 COFF 格式和辨識項 (所使用的其他多載<xref:System.Reflection.Assembly.Load%2A>) 無關的 XAML 的組件載入之用; 所有的負載資訊必須顯示為字串。  
  
 指定組件的公開金鑰是 XAML 的安全性，或移除可能模稜兩可，可以存在於，如果組件載入的簡單名稱，或預先快取或應用程式網域中存在很有用的技巧。 如需詳細資訊，請參閱 < [XAML 安全性考量](../../../docs/framework/xaml-services/xaml-security-considerations.md)。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>在 XAML 服務 API 的 XAML 命名空間宣告  
 在 XAML 服務 API 中的 XAML 命名空間宣告由<xref:System.Xaml.NamespaceDeclaration>物件。 如果您宣告在程式碼中的 XAML 命名空間，您呼叫<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>建構函式。 `ns`和`prefix`參數會指定為字串，並提供這些參數的輸入對應至 XAML 命名空間識別項和 XAML 命名空間前置詞的定義，為本主題先前所提供。  
  
 如果您正在檢查 XAML 節點資料流的一部分或透過 XAML 類型系統中，其他存取 XAML 命名空間資訊<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType>報告的 XAML 命名空間識別項，以及<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType>報告 XAML 命名空間前置詞。  
  
 XAML 節點資料流，XAML 命名空間資訊可以顯示為 XAML 節點之前它所套用的實體。 這包括其中的 XAML 命名空間資訊之前的情況下`StartObject`的 XAML 根項目。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
 使用.NET Framework XAML 服務 API 的許多情況下，至少一個 XAML 命名空間宣告必須要有，，和宣告必須包含或參考的 XAML 結構描述內容所需的資訊。 XAML 命名空間必須指定要載入，或協助解決命名空間和已經載入或已知的 XAML 結構描述內容的組件內的特定類型的組件。  
  
 若要產生 XAML 節點資料流，XAML 型別資訊必須可透過 XAML 結構描述內容。 無法判斷的 XAML 型別資訊，而不需要先決定要建立的每個節點的相關 XAML 命名空間。 此時，尚未，建立任何類型的執行個體，但 XAML 結構描述內容可能需要查閱從定義組件和備份類型的資訊。 例如，若要處理的標記`<Party><PartyFavor/></Party>`，XAML 結構描述內容必須能夠判斷名稱和型別`ContentProperty`的`Party`，並因此也必須知道的 XAML 命名空間資訊`Party`和`PartyFavor`。 如果是預設 XAML 結構描述內容中，靜態反映報告的大部分 XAML 類型系統資訊所需的節點資料流中產生 XAML 型別節點。  
  
 若要從 XAML 節點資料流中產生物件圖形，XAML 命名空間宣告必須存在原始標記中使用，而且記錄在 XAML 節點資料流的每個 XAML 前置詞。 到目前為止，已建立執行個體，且會發生，則為 true 的型別對應行為。  
  
 如果您要預先填入的 XAML 命名空間的資訊，請在未在標記中，定義您想要使用的 XAML 結構描述內容的 XAML 命名空間的情況下您可以使用其中一種技術是宣告中的 XML 命名空間宣告<xref:System.Xml.XmlParserContext>的<xref:System.Xml.XmlReader>. 然後使用該<xref:System.Xml.XmlReader>做為輸入的 XAML 讀取器建構函式或<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>。  
  
 屬性是與相關的.NET Framework XAML 服務中處理的 XAML 命名空間的其他兩個 API<xref:System.Windows.Markup.XmlnsDefinitionAttribute>和<xref:System.Windows.Markup.XmlnsPrefixAttribute>。 這些屬性套用至組件。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 會使用 XAML 結構描述內容來解譯包含 URI 的任何 XAML 命名空間宣告。 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 會使用發出 XAML，以便可以序列化特定的 XAML 命名空間，以可預測的前置詞的工具。 如需詳細資訊，請參閱 < [XAML-Related 自訂類型和程式庫的 CLR 屬性](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="see-also"></a>另請參閱  
 [認識 XAML 節點資料流結構和概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
