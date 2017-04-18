---
title: "XAML Namespaces for .NET Framework XAML Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# XAML Namespaces for .NET Framework XAML Services
XAML 命名空間是 XML 命名空間定義概念的延伸。  與 XML 命名空間類似，您可以在標記中使用 `xmlns` 屬性來定義 XAML 命名空間。  XAML 命名空間在 XAML 節點資料流和其他 XAML 服務 API 中也有代表項目。  本主題將定義 XAML 命名空間概念，並說明 XAML 命名空間的定義方式，以及 XAML 結構描述內容和其他 .NET Framework XAML 服務部分使用 XAML 命名空間的方式。  
  
## XML 命名空間與 XAML 命名空間  
 XAML 命名空間是特製的 XML 命名空間，這點就如同 XAML 是特製形式的 XML，而在標記中使用基本的 XML 形式。  在標記中，您會透過對項目套用的 `xmlns` 屬性，宣告 XAML 命名空間與其對應。  `xmlns` 宣告可以位於宣告 XAML 命名空間的同一個項目上。  對項目建立的 XAML 命名空間宣告對於該項目、該項目的所有屬性以及該項目的所有子項目都有效。  屬性可以與屬性所在的項目使用不同的 XAML 命名空間，只要屬性名稱本身就參考了前置詞做為其屬性名稱在標記中的一部分。  
  
 XAML 命名空間與 XML 命名空間的區別在於 XML 命名空間可以用來參考結構描述，也可以只用來區分實體。  對於 XAML 而言，XAML 中使用的型別和成員最終必須解析成支援型別，而 XML 結構描述概念則不完全適用於此功能。  XAML 命名空間包含 XAML 結構描述內容必須擁有才能執行此型別對應的資訊。  
  
## XAML 命名空間元件  
 XAML 命名空間定義具有兩個元件：前置詞和識別項。  在標記中宣告 XAML 命名空間，或在 XAML 型別系統中定義 XAML 命名空間時，這些元件都存在。  
  
 前置詞可以是 [XML 1.0 的 W3C 命名空間規格](http://go.microsoft.com/fwlink/?LinkID=161735) \(英文\) 所允許的任何字串。  依照慣例，前置詞通常是極短的字串，因為前置詞在典型標記檔中會重複許多次。  某些會在多個 XAML 實作中使用的 XAML 命名空間會使用特定的慣用前置詞。  例如，XAML 語言 XAML 命名空間通常以前置詞 `x` 來對應。  您可以定義預設的 XAML 命名空間，其前置詞雖未提供於定義中，但若由 .NET Framework XAML 服務 API 定義或查詢，將會以空白字串表示。  預設 XAML 命名空間通常是刻意選擇的，以便實作 XAML 的技術以及其情節和詞彙能夠在標記中省略最多的前置詞。  
  
 識別項可以是 [XML 1.0 的 W3C 命名空間規格](http://go.microsoft.com/fwlink/?LinkID=161735) \(英文\) 所允許的任何字串。  依照慣例，XML 命名空間或 XAML 命名空間的識別項通常是以 URI 形式 \(通常是加上通訊協定限定詞的絕對 URI\) 提供。  通常，用於定義特定 XAML 詞彙的版本資訊會隱含為路徑字串的一部分。  XAML 命名空間除了採用 XML URI 慣例外，還多採用一項識別項慣例。  在 XAML 命名空間中，此識別項會傳達 XAML 結構描述內容所需的資訊，以便解析以該 XAML 命名空間下的項目形式指定的型別，或解析成員的屬性。  
  
 為了將資訊傳達至 XAML 結構描述內容的目的，XAML 命名空間的識別項可能仍為 URI 形式。  但是在此情況下，URI 也會宣告為特定一個或多個組件中的比對識別項。  這是透過在組件中以 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 將組件屬性化達成。  .NET Framework XAML 服務中的預設 XAML 結構描述內容可支援此種在屬性化組件中識別 XAML 命名空間和支援 CLR 式型別解析行為的方法。  更廣泛地說，此慣例可用於 XAML 結構描述內容納入 CLR 或是以預設 XAML 結構描述內容為基礎 \(此為讀取 CLR 組件中的 CLR 屬性時所需\) 的情況。  
  
 若要識別 XAML 命名空間，還可以使用一個慣例，那就是指定 CLR 命名空間和用於定義型別的組件。  當包含型別的組件中不存在任何 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 屬性時，會使用此慣例。  此慣例可能比 URI 慣例更複雜，而且也可能有模稜兩可和重複情形，因為參考組件的方法有很多種。  
  
 使用 CLR 命名空間和組件慣例的最基本識別項形式如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` 和 `; assembly=` 是此語法的常值元件。  
  
 *clrnsName* 是用於識別 CLR 命名空間的字串名稱。  此字串名稱內含的任何點字元 \(.\) 會提供有關 CLR 命名空間及其與其他 CLR 命名空間之關聯性的暗示。  
  
 *assemblyShortName* 是組件的字串名稱，該組件定義了 XAML 中的有用型別。  要透過所宣告的 XAML 命名空間存取的型別應已定義在該組件中，並已特別宣告在 *clrnsName* 所指定的 CLR 命名空間內。  此字串名稱通常與 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName> 所報告的資訊一致。  
  
 CLR 命名空間和組件慣例的更完整定義如下所示：  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* 代表任何可以合法做為 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> 輸入的字串。  這個字串可以包含文化特性、公用金鑰或版本資訊 \(這些概念的定義已定義於 <xref:System.Reflection.Assembly> 的參考主題中\)。  COFF 格式和辨識項 \(由 <xref:System.Reflection.Assembly.Load%2A> 的其他多載使用\) 與 XAML 組件載入目的無關；所有載入資訊都必須以字串形式呈現。  
  
 如果組件是以簡單名稱載入，或預先存在於快取或應用程式定義域中，就 XAML 安全性而言，或是為了移除可能存在的模稜兩可情況，指定組件的公用金鑰是很實用的技巧。  如需詳細資訊，請參閱 [XAML Security Considerations](../../../docs/framework/xaml-services/xaml-security-considerations.md)。  
  
## XAML 服務 API 中的 XAML 命名空間宣告  
 在 XAML 服務 API 中，XAML 命名空間宣告是以 <xref:System.Xaml.NamespaceDeclaration> 物件表示。  如果您要在程式碼中宣告 XAML 命名空間，請呼叫 <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> 建構函式。  `ns` 和 `prefix` 參數是以字串形式指定，在這些參數中所提供的輸入對應於 XAML 命名空間識別項與 XAML 命名空間前置詞的定義 \(如本主題先前所提供\)。  
  
 如果您要在 XAML 節點資料流中或透過其他存取 XAML 型別系統的方式檢查 XAML 命名空間資訊，<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=fullName> 會報告 XAML 命名空間識別項，而 <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=fullName> 會報告 XAML 命名空間前置詞。  
  
 在 XAML 節點資料流中，XAML 命名空間資訊會顯示為 XAML 節點，位置就在套用該節點的實體之前。  這包括 XAML 命名空間資訊位於 XAML 根項目的 `StartObject` 之前的情況。  如需詳細資訊，請參閱[Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)。  
  
 在許多使用 .NET Framework XAML 服務 API 的情節中，至少應有一個 XAML 命名空間宣告，而此宣告必須包含或參考 XAML 結構描述內容所需的資訊。  XAML 命名空間必須指定要載入的組件，或必須協助解析 XAML 結構描述內容所載入或知悉的命名空間和組件內的特定型別。  
  
 為了產生 XAML 節點資料流，必須可透過 XAML 結構描述內容取得 XAML 型別資訊。  對於每個要建立的節點，不先判斷相關的 XAML 命名空間，就無法判斷 XAML 型別資訊。  雖然這個時候尚未建立任何型別的執行個體，但 XAML 結構描述內容可能需要查詢定義組件和支援型別中的資訊。  例如，為了處理標記 `<Party><PartyFavor/></Party>`，XAML 結構描述內容必須能夠判斷 `Party` 之 `ContentProperty` 的名稱和型別，因而也必須知道 `Party` 和 `PartyFavor` 的 XAML 命名空間資訊。  就預設 XAML 結構描述內容而言，靜態反映會報告在節點資料流中產生 XAML 型別節點時所需的許多 XAML 型別系統資訊。  
  
 為了從 XAML 節點資料流產生物件圖形，每個用於原始標記並記錄於 XAML 節點資料流中的 XAML 前置詞都必須有 XAML 命名空間宣告存在。  這時，就會建立執行個體，並出現真正的型別對應行為。  
  
 如果您需要預先填入 XAML 命名空間資訊，以防萬一 XAML 結構描述內容使用的 XAML 命名空間未定義在標記中，您可以使用的其中一個技巧就是在 <xref:System.Xml.XmlReader> 的 <xref:System.Xml.XmlParserContext> 中宣告 XML 命名空間。  然後，使用該 <xref:System.Xml.XmlReader> 做為 XAML 讀取器建構函式 \(或 <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=fullName>\) 的輸入。  
  
 .NET Framework XAML 服務中與處理 XAML 命名空間有關的另外兩個 API 是 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 和 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 屬性。  這些屬性會套用至組件。  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 會由 XAML 結構描述內容用來解譯任何包含 URI 的 XAML 命名空間宣告。  <xref:System.Windows.Markup.XmlnsPrefixAttribute> 會由發出 XAML 的工具使用，以便使用可預測的前置詞來序列化特定 XAML 命名空間。  如需詳細資訊，請參閱[XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## 請參閱  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)