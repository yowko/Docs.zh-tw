---
title: "定義可搭配 .NET Framework XAML 服務使用的自訂類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7cce479c7c7a5f6c7112f08f1e15f3bc7e4d366
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>定義可搭配 .NET Framework XAML 服務使用的自訂類型
當您定義了商務物件的自訂型別，或在特定架構上沒有相依性的類型時，但有特定的 XAML，您可以遵循的最佳作法。 如果您依照這些作法，可以發現 XAML 特性，您的型別.NET Framework XAML 服務和 XAML 讀取器和 XAML 寫入器，並提供適當的表示，使用 XAML 類型系統的 XAML 節點資料流。 本主題說明類型定義、 成員定義和 CLR 設定其屬性的型別或成員的最佳作法。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>建構函式模式和 xaml 的類型定義  
 若要為物件項目在 XAML 中具現化，自訂的類別必須符合下列需求：  
  
-   自訂的類別必須是公用的而且必須公開預設 （無參數） 公用建構函式。 (如需結構相關附註，請參閱下節)。  
  
-   自訂類別不能巢狀的類別。 「 點 」 的完整名稱的路徑中的額外類別命名空間除法模稜兩可，並干擾到其他的 XAML 功能，例如附加屬性。  
  
 如果物件可以具現化為物件項目，建立的物件可以填滿屬性項目表單的任何屬性，取得其基礎類型為物件。  
  
 您仍然可以提供物件值的類型不符合這些條件，如果您啟用的值轉換器。 如需詳細資訊，請參閱[類型轉換器和 XAML 的標記延伸](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
### <a name="structures"></a>結構  
 結構都可以在 XAML 中，由 CLR 定義。 這是因為 CLR 編譯器隱含地建立結構的預設建構函式。 這個建構函式會初始化為其預設值的所有屬性值。  
  
 在某些情況下，您可能不想要建構的預設行為的結構。 這可能是因為結構用來填滿值和函式在概念上，於聯集。 為等位，包含的值可能會有互為獨佔模式的解譯，並因此，其屬性都可設定。 舉例來說，這種結構中的 WPF 詞彙是<xref:System.Windows.GridLength>。 這類結構應該實作類型轉換器，可以藉由建立不同的解譯或結構值的模式字串慣例以屬性形式表示值。 此結構也應該透過非預設建構函式進行程式碼建構來公開類似行為。  
  
### <a name="interfaces"></a>介面  
 介面可用來當做基礎類型的成員。 XAML 類型系統會檢查可指派的清單，並預期提供做為值的物件，可以指派給介面。 沒有介面如何必須呈現為 XAML 型別，只要相關指派的型別支援 XAML 建構需求的概念。  
  
### <a name="factory-methods"></a>Factory 方法  
 Factory 方法，是 XAML 2009 功能。 它們修改 XAML 的主體物件必須具有預設建構函式。 本主題中未記載 factory 方法。 請參閱[X:factorymethod 指示詞](../../../docs/framework/xaml-services/x-factorymethod-directive.md)。  
  
## <a name="enumerations"></a>列舉  
 列舉有 XAML 原生類型轉換行為。 列舉常數的名稱，在 XAML 中指定對基礎的列舉類型，判斷已解決，然後返回 XAML 物件寫入器的列舉值。  
  
 XAML 支援的旗標樣式的使用方式的列舉型別與<xref:System.FlagsAttribute>套用。 如需詳細資訊，請參閱[XAML 語法的詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。 ([XAML 語法的詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)寫入的 WPF 對象，但該主題中的資訊很並非專門針對特定的實作架構的 xaml 相關。)  
  
## <a name="member-definitions"></a>成員的定義  
 類型可以定義 XAML 用法的成員。 很可能是 XAML 使用，即使該特定的類型不是可使用 XAML 的成員定義的類型。 這可能是因為 CLR 繼承。 只要繼承成員的型別支援 XAML 用法為型別，而且該成員支援其基礎類型的 XAML 用法或具有原生可用的 XAML 語法，該成員是 XAML 可用。  
  
### <a name="properties"></a>屬性  
 如果您定義為公用的 CLR 屬性，使用一般的 CLR 屬性`get`和`set`存取子模式和適當語言 keywording，XAML 類型系統可以報告提供適當的資訊與成員屬性<xref:System.Xaml.XamlMember>屬性，例如<xref:System.Xaml.XamlMember.IsReadPublic%2A>和<xref:System.Xaml.XamlMember.IsWritePublic%2A>。  
  
 特定的屬性可以藉由套用可讓文字語法<xref:System.ComponentModel.TypeConverterAttribute>。 如需詳細資訊，請參閱[類型轉換器和 XAML 的標記延伸](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 在文字語法或原生 XAML 的轉換不存在，進一步間接取值，例如標記延伸使用方式，屬性類型不存在 (<xref:System.Xaml.XamlMember.TargetType%2A> xaml 類型系統) 必須能夠藉由將 t 返回 XAML 物件寫入器的執行個體目標類型為 CLR 型別。  
  
 如果使用 XAML 2009 [X:reference 標記延伸](../../../docs/framework/xaml-services/x-reference-markup-extension.md)可以用來提供值，如果不符合先前的考量; 不過，這是多個類型定義問題比使用問題。  
  
### <a name="events"></a>事件  
 如果您定義為公用的 CLR 事件的事件，XAML 類型系統可以報告事件的成員為<xref:System.Xaml.XamlMember.IsEvent%2A>為`true`。 傳入的事件處理常式不是.NET Framework XAML 服務的功能; 範圍內這會保留給特定架構和實作。  
  
### <a name="methods"></a>方法  
 方法的內嵌程式碼不是預設的 XAML 功能。 在大部分情況下您不要直接參照方法成員從 XAML，和方法，在 XAML 中的角色只是為了提供支援的特定 XAML 模式。 [X:factorymethod 指示詞](../../../docs/framework/xaml-services/x-factorymethod-directive.md)是例外狀況。  
  
### <a name="fields"></a>欄位  
 CLR 設計指導方針不鼓勵非靜態欄位。 靜態欄位，您可以存取靜態欄位值只能透過[X:static 標記延伸](../../../docs/framework/xaml-services/x-static-markup-extension.md); 在此情況下您不會進行任何特殊作業中要公開 （expose） 的欄位的 CLR 定義[X:static](../../../docs/framework/xaml-services/x-static-markup-extension.md)使用方式。  
  
## <a name="attachable-members"></a>可附加成員  
 可附加成員是為 XAML 透過模式可公開存取子方法上定義的類型。 定義類型本身不必能夠 XAML-當做物件。 事實上，常見的模式是來宣告其角色是在服務類別來擁有可附加成員和實作相關的行為，但是不做任何其他功能，例如 UI 表示法。 下列章節將預留位置的*PropertyName*代表您可附加成員的名稱。 該名稱必須是有效的[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。  
  
 留意這些模式和其他方法的類型之間發生名稱衝突。 如果有符合模式的其中一個成員，它可以解譯為可附加成員使用量路徑在 XAML 處理器即使這不是您的意圖。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName 存取子  
 `Get`<屬性名稱> 存取子的簽章必須是︰  
  
 `public static object Get` <屬性名稱> `(object`  `target` `)`  
  
-   `target` 物件可以指定為實作中的更特定類型。 您可以使用這個限定範圍的可附加的成員; 使用方式您想要的範圍之外的使用方式，將會擲回，然後由 XAML 剖析錯誤顯示無效的轉型例外狀況。 參數名稱`target`，就不需要，但是名為`target`依照慣例，在大部分的實作。  
  
-   傳回值可以指定為實作中的更特定類型。  
  
 若要支援<xref:System.ComponentModel.TypeConverter>對於屬性使用方式的可附加的成員，已啟用的文字語法套用<xref:System.ComponentModel.TypeConverterAttribute>至`Get` *PropertyName*存取子。 將套用至`get`而不是`set`似乎直覺性; 不過，這個慣例可以支援概念的唯讀可附加成員都是可序列化，這是在設計工具的情況下很有用。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName 存取子  
 集合的簽章*PropertyName*存取子必須是：  
  
 `public static void Set` <屬性名稱> `(object`  `target` `, object`  `value` `)`  
  
-   `target`物件可以指定為更特定的類型，在您實作中，與相同邏輯後果，如上一節中所述。  
  
-   `value` 物件可以指定為實作中的更特定類型。  
  
 請記住，此方法的值是來自 XAML 用法，通常是以屬性形式的輸入。 從屬性格式必須是值轉換器支援文字語法中，而且您屬性`Get` *PropertyName*存取子。  
  
### <a name="attachable-member-stores"></a>可附加成員存放區  
 存取子方法不通常不足以提供的方法將可附加成員值放置物件圖形，或擷取值，超出物件圖形，並將其正確序列化。 若要提供這項功能，`target`的上一個存取子的簽章中的物件必須能夠儲存的值。 儲存機制應該和成員是可附加至目標的可附加成員不在成員清單中的可附加成員原則一致。 .NET framework XAML 服務提供的實作方法，對於可附加成員會儲存應用程式開發介面透過<xref:System.Xaml.IAttachedPropertyStore>和<xref:System.Xaml.AttachablePropertyServices>。 <xref:System.Xaml.IAttachedPropertyStore>可由 XAML 寫入器來探索的存放區實作，並應該是型別上實作`target`存取子。 靜態<xref:System.Xaml.AttachablePropertyServices>Api 的存取子中，主體內使用，而且參考的可附加成員及其<xref:System.Xaml.AttachableMemberIdentifier>。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 相關 CLR 屬性  
 正確地設定其屬性，您的類型、 成員和組件是很重要的報表以.NET Framework XAML 服務 XAML 類型系統資訊的順序。 這是相關，如果您想要的 XAML 系統，直接根據.NET Framework XAML 服務 XAML 讀取器和 XAML 寫入器，用於您的型別，或如果您定義，或使用 XAML 使用的架構為基礎的 XAML 讀取器和 XAML 寫入器。  
  
 如需每個 XAML 相關屬性的 XAML 支援，您的自訂型別相關的清單，請參閱[XAML-Related CLR 屬性之自訂類型和程式庫](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## <a name="usage"></a>使用量  
 使用自訂類型需要標記作者必須對應包含自訂類型的組件和 CLR 命名空間的前置詞。 此程序不會記載於本主題中。  
  
## <a name="access-level"></a>存取層級  
 XAML 可提供方法來載入和執行個體化類型具有`internal`存取層級。 這項功能被提供讓使用者程式碼可以定義自己的型別，再執行個體化這些類別，從標記，也是相同的使用者程式碼領域的一部分。  
  
 WPF 的範例是當使用者程式碼會定義<xref:System.Windows.Controls.UserControl>，用來重構 UI 行為，但不是可能會隱含宣告的支援類別，以任何可能的延伸模組機制的一部分`public`存取層級。 這類<xref:System.Windows.Controls.UserControl>可以使用宣告`internal`存取支援程式碼會編譯從中它為 XAML 型別參考相同組件。  
  
 應用程式會在完全信任下載入的 XAML，並使用<xref:System.Xaml.XamlObjectWriter>，載入具有類別`internal`存取層級一定會啟用。  
  
 在部分信任下載入 XAML 的應用程式，您可以使用控制存取層級特性<xref:System.Xaml.Permissions.XamlAccessLevel>應用程式開發介面。 此外，延遲機制 （例如 WPF 範本系統） 必須能夠傳播存取層級權限，並保留供最終的執行的階段評估;這藉由傳遞內部處理<xref:System.Xaml.Permissions.XamlAccessLevel>資訊。  
  
### <a name="wpf-implementation"></a>WPF 實作  
 WPF XAML 使用部分信任存取模型，如果 BAML 載入在部分信任下，存取限於<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>BAML 來源組件。 對於延遲，WPF 會使用<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>做為傳遞的存取層級資訊的機制。  
  
 在 WPF XAML 術語*內部型別*是由相同組件也包含參考的 XAML 定義的類型。 這種型別可以對應透過故意省略組件的 XAML 命名空間 = 部分的對應，例如`xmlns:local="clr-namespace:WPFApplication1"`。  如果 BAML 參考內部的型別和型別具有`internal`存取層級，這會產生`GeneratedInternalTypeHelper`組件的類別。 如果您想要避免`GeneratedInternalTypeHelper`，您可能必須使用`public`存取層級，或必須相關的類別，分解到不同的組件並讓這個組件相依。  
  
## <a name="see-also"></a>請參閱  
 [自訂類型和程式庫的 XAML 相關 CLR 屬性](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [XAML Services](../../../docs/framework/xaml-services/index.md)
