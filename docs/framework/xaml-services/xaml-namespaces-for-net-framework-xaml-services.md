---
title: .NET Framework XAML 服務的 XAML 命名空間
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837164"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML 服務的 XAML 命名空間
XAML 命名空間是在 XML 命名空間的定義上展開的概念。 類似于 XML 命名空間，您可以使用標記中的 `xmlns` 屬性來定義 XAML 命名空間。 XAML 命名空間也會在 XAML 節點資料流程和其他 XAML 服務 Api 中表示。 本主題會定義 XAML 命名空間概念，並描述 xaml 命名空間的定義方式，以及 XAML 架構內容和 .NET Framework XAML 服務的其他層面所使用的方法。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML 命名空間和 XAML 命名空間  
 XAML 命名空間是特殊的 XML 命名空間，就如同 XAML 是特殊形式的 XML，而且會針對其標記使用基本的 XML 格式。 在標記中，您可以透過套用至專案的 `xmlns` 屬性來宣告 XAML 命名空間及其對應。 `xmlns` 宣告可以對 XAML 命名空間宣告所在的相同元素進行。 對專案所做的 XAML 命名空間宣告，對該元素、該專案的所有屬性，以及該專案的所有子系都是有效的。 屬性可以使用與包含屬性的專案不相同的 XAML 命名空間，只要屬性名稱本身會在標記中將前置詞參考為其屬性名稱的一部分。  
  
 XAML 命名空間與 XML 命名空間的區別在於，XML 命名空間可能會用來參考架構，也可能用來區別實體。 對於 XAML，XAML 中所使用的類型和成員最終必須解析成支援類型，而 XML 架構概念不適用於這項功能。 XAML 命名空間包含 XAML 架構內容必須可用才能執行此類型對應的資訊。  
  
## <a name="xaml-namespace-components"></a>XAML 命名空間元件  
 XAML 命名空間定義有兩個元件：前置詞和識別碼。 當 XAML 命名空間在標記中宣告，或在 XAML 類型系統中定義時，每個元件都存在。  
  
 前置詞可以是[XML 1.0 規格中 W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)所允許的任何字串。 依照慣例，前置詞通常是非常短的字串，因為前置詞會在一般標記檔案中重複多次。 某些要在多個 XAML 執行中使用的 XAML 命名空間，會使用特定的傳統首碼。 例如，XAML 語言 XAML 命名空間通常會使用前置詞 `x`來對應。 您可以定義預設的 XAML 命名空間，其中的前置詞不會在定義中提供，但如果已定義或查詢 by.NET Framework XAML 服務 API，則會表示為空字串。 一般而言，會刻意選擇預設的 XAML 命名空間，藉由 XAML 執行技術及其案例和詞彙，來提升最大化的前置詞省略標記數量。  
  
 此識別碼可以是[XML 1.0 規格中 W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)所允許的任何字串。 依照慣例，XML 命名空間或 XAML 命名空間的識別碼通常是以 URI 形式提供，通常是以通訊協定限定的絕對 URI。 通常，定義特定 XAML 詞彙的版本資訊會隱含為路徑字串的一部分。 XAML 命名空間會在 XML URI 慣例以外新增額外的識別碼慣例。 對於 XAML 命名空間，識別碼會傳達 XAML 架構內容所需的資訊，以便解析指定為該 XAML 命名空間下之元素的類型，或將屬性解析為成員。  
  
 基於將資訊傳遞至 XAML 架構內容的目的，XAML 命名空間的識別碼可能仍然是 URI 形式。 不過，在此情況下，URI 也會宣告為特定元件或元件清單中的相符識別碼。 這項作業是在元件中完成，方法是使用 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>將元件的特性化。 .NET Framework XAML 服務中的預設 XAML 架構內容支援識別 XAML 命名空間，以及支援屬性化元件中以 CLR 為基礎之類型解析行為的這個方法。 更常見的情況是，此慣例適用于 XAML 架構內容併入 CLR 的情況，或是以預設 XAML 架構內容為基礎，這是從 CLR 元件讀取 CLR 屬性時的必要功能。  
  
 XAML 命名空間也可以透過與 CLR 命名空間和類型定義元件通訊的慣例來識別。 當包含類型的元件中沒有 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 屬性存在時，就會使用這個慣例。 這個慣例可能比 URI 慣例更為複雜，而且也有可能發生不明確和重複的情況，因為有多種方式可以參考元件。  
  
 使用 CLR 命名空間和元件慣例之識別碼的最基本形式如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` 和 `; assembly=` 是語法的常值元件。  
  
 *clrnsName*是識別 CLR 命名空間的字串名稱。 這個字串名稱包含任何內部的點字元（.），可提供有關 CLR 命名空間和其與其他 CLR 命名空間之關聯的提示。  
  
 *assemblyShortName*是定義 XAML 中有用類型之元件的字串名稱。 要透過宣告的 XAML 命名空間存取的類型，必須由元件定義，並在*clrnsName*所指定的 CLR 命名空間中特別宣告。 此字串名稱通常會與 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>所報告的資訊類似。  
  
 更完整的 CLR 命名空間和元件慣例定義如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName*表示任何合法做為 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> 輸入的字串。 這個字串可以包含文化特性、公開金鑰或版本資訊（這些概念的定義定義于 <xref:System.Reflection.Assembly>的參考主題中）。 COFF 格式和辨識項（由 <xref:System.Reflection.Assembly.Load%2A>的其他多載所使用）與 XAML 元件載入用途無關。所有的載入資訊都必須以字串形式呈現。  
  
 指定元件的公開金鑰是適用于 XAML 安全性的實用技巧，或用於移除如果元件是以簡單名稱載入，或是預先存在於快取或應用程式域中，可能會有的模糊。 如需詳細資訊，請參閱[XAML 安全性考慮](xaml-security-considerations.md)。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML 服務 API 中的 XAML 命名空間宣告  
 在 XAML 服務 API 中，XAML 命名空間宣告是以 <xref:System.Xaml.NamespaceDeclaration> 物件來表示。 如果您要在程式碼中宣告 XAML 命名空間，您可以呼叫 <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> 的函式。 `ns` 和 `prefix` 參數會指定為字串，而提供給這些參數的輸入會對應至 XAML 命名空間識別碼和 XAML 命名空間前置詞的定義，如本主題先前所提供。  
  
 如果您要在 XAML 節點資料流程中檢查 XAML 命名空間資訊，或透過其他方式存取 XAML 類型系統，<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> 會報告 XAML 命名空間識別碼，而 <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> 會報告 XAML 命名空間前置詞。  
  
 在 XAML 節點資料流程中，XAML 命名空間資訊可以顯示為 XAML 節點，在它所套用的實體之前。 這包括 XAML 命名空間資訊在 XAML 根項目 `StartObject` 之前的情況。 如需詳細資訊，請參閱 [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md)。  
  
 針對許多使用 .NET Framework XAML 服務 API 的案例，至少應有一個 XAML 命名空間宣告存在，而且宣告必須包含或參考 XAML 架構內容所需的資訊。 XAML 命名空間必須指定要載入的元件，或協助解析已載入或已由 XAML 架構內容所識別的命名空間和元件中的特定類型。  
  
 為了產生 XAML 節點資料流程，XAML 型別資訊必須可供使用，透過 XAML 架構內容。 無法判斷 XAML 類型資訊，而不需要先針對每個要建立的節點判斷相關的 XAML 命名空間。 此時，尚未建立任何類型的實例，但 XAML 架構內容可能需要從定義元件和支援類型查詢資訊。 例如，為了處理標記 `<Party><PartyFavor/></Party>`，XAML 架構內容必須能夠判斷 `Party``ContentProperty` 的名稱和類型，因此也必須知道 `Party` 和 `PartyFavor`的 XAML 命名空間資訊。 在預設的 XAML 架構內容中，靜態反映會報告在節點資料流程中產生 XAML 型別節點所需的許多 XAML 型別系統資訊。  
  
 為了從 XAML 節點資料流程產生物件圖形，在原始標記中使用的每個 XAML 前置詞都必須有 XAML 命名空間宣告，並記錄在 XAML 節點資料流程中。 此時，會建立實例，並且會發生真正的類型對應行為。  
  
 如果您需要預先填入 XAML 命名空間資訊，在您想要使用 XAML 架構內容的 XAML 命名空間未在標記中定義的情況下，您可以使用的一項技巧是在 <xref:System.Xml.XmlReader>的 <xref:System.Xml.XmlParserContext> 中宣告 XML 命名空間宣告。 然後使用該 <xref:System.Xml.XmlReader> 做為 XAML 讀取器函式的輸入，或 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>。  
  
 與 .NET Framework XAML 服務中的 XAML 命名空間處理相關的其他兩個 API 是 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 和 <xref:System.Windows.Markup.XmlnsPrefixAttribute>屬性。 這些屬性適用于元件。 XAML 架構內容會使用 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 來解讀任何包含 URI 的 XAML 命名空間宣告。 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 是由發出 XAML 的工具所使用，因此特定的 XAML 命名空間可以使用可預測的前置詞進行序列化。 如需詳細資訊，請參閱[自訂類型和程式庫的 XAML 相關 CLR 屬性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="see-also"></a>請參閱

- [認識 XAML 節點資料流結構和概念](understanding-xaml-node-stream-structures-and-concepts.md)
