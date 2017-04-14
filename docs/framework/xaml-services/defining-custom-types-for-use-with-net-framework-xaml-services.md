---
title: "Defining Custom Types for Use with .NET Framework XAML Services | Microsoft Docs"
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
  - "defining custom types [XAML Services]"
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# Defining Custom Types for Use with .NET Framework XAML Services
如果您定義的自訂型別是商務物件或是對特定架構不具相依性的型別，則您在使用 XAML 時，可以遵循特定的最佳作法。  如果您遵循這些作法，.NET Framework XAML 服務及其 XAML 讀取器與 XAML 寫入器將可探索型別的 XAML 特性，並透過 XAML 型別系統讓您的型別在 XAML 節點資料流中能有正確的顯示。  本主題將說明型別定義、成員定義、以及型別或成員的 CLR 屬性設定。  
  
## XAML 的建構函式模式與型別定義  
 自訂類別必須符合下列需求，才能具現化為 XAML 中的物件項目：  
  
-   自訂類別必須是公用的，且必須公開預設的 \(無參數\) 公用建構函式   \(如需有關結構的注意事項，請參閱下一節\)。  
  
-   自訂類別不可以是巢狀類別。  完整名稱路徑中多餘的「點號」會使「類別\-命名空間」區分模糊不清，並且妨礙其他 XAML 功能，如附加屬性。  
  
 如果某物件可具現化為物件項目，則建立的物件將可填入任何以該物件做為其基礎型別之屬性的屬性項目格式。  
  
 如果您啟用值轉換子，則仍可為不符合這些準則的型別提供物件值。  如需詳細資訊，請參閱 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
### 結構  
 結構一律可依 CLR 定義在 XAML 中建構。  這是因為 CLR 編譯器會隱含地建立結構的預設建構函式。  此建構函式會將所有屬性值初始化為其預設值。  
  
 在某些情況下，預設建構行為並不適用於結構。  這可能是因為結構預定應以等位的概念填入值與函式。  採用等位方式時，包含的值可能有互斥解譯，因此其中沒有可設定的屬性。  WPF 詞彙中的 <xref:System.Windows.GridLength>，即屬此類結構。  此類結構應該實作型別轉換子，以使用為結構的值建立不同解譯或模式的字串慣例，讓值能夠以屬性形式表示。  而結構也應該透過非預設的建構函式，公開程式碼建構的類似行為。  
  
### 介面  
 介面可以做為成員的基礎型別。  XAML 型別系統會檢查可指派的清單，並預期以值形式提供的物件可指派給介面。  只要相關的可指派型別支援 XAML 建構需求，介面就無須以特定的方式表示為 XAML 型別。  
  
### Factory 方法  
 Factory 方法為 XAML 2009 功能。  這類方法可修改物件必須具有預設建構函式的 XAML 準則。  Factory 方法不在本主題的討論之列。  請參閱 [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md)。  
  
## 列舉  
 列舉具有 XAML 原生型別轉換行為。  XAML 中所指定的列舉常數名稱會根據基礎列舉型別進行解析，並將列舉值傳回給 XAML 物件寫入器。  
  
 XAML 支援在套用 <xref:System.FlagsAttribute> 的情況下，對列舉使用旗標樣式。  如需詳細資訊，請參閱 [XAML 語法詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  \([XAML 語法詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) 是針對 WPF 使用者而撰寫的，但該主題中的資訊大多是有關於並非專屬於特定實作架構的 XAML。\)  
  
## 成員定義  
 型別可以定義 XAML 用法的成員。  即使型別本身不適用於 XAML，該型別仍可定義適用於 XAML 的成員。  可以這麼做是因為 CLR 繼承。  只要有部分繼承成員的型別支援以 XAML 用法做為型別，且該成員支援以 XAML 用法做為其基礎型別，或具有可用的原生 XAML 語法，則該成員適用於 XAML。  
  
### 屬性  
 如果您使用典型的 CLR `get` 和 `set` 存取子模式和適當語言關鍵字，將屬性定義為公用 CLR 屬性，則 XAML 型別系統可使用為 <xref:System.Xaml.XamlMember> 屬性所提供的適當資訊 \(如 <xref:System.Xaml.XamlMember.IsReadPublic%2A> 和 <xref:System.Xaml.XamlMember.IsWritePublic%2A>\)，將屬性報告為成員。  
  
 特定屬性可在套用 <xref:System.ComponentModel.TypeConverterAttribute> 後啟用文字語法。  如需詳細資訊，請參閱 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 如果缺少文字語法或原生 XAML 轉換，並且缺少進一步的間接取值 \(如標記延伸用法\)，則屬性的型別 \(在 XAML 型別系統中為 <xref:System.Xaml.XamlMember.TargetType%2A>\) 必須能夠將目標型別視為 CLR 型別，以將執行個體傳回至 XAML 物件寫入器。  
  
 在使用 XAML 2009 時，如果不符合前述考量事項，仍可使用 [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md) 來提供值，但這已偏向於用法問題，而非型別定義問題。  
  
### 事件  
 如果您將事件定義為公用 CLR 事件，則 XAML 型別系統可將 <xref:System.Xaml.XamlMember.IsEvent%2A> 設為 `true`，以將事件報告為成員。  連接事件處理常式不在 .NET Framework XAML 服務的功能範疇內；這些功能由特定的架構與實作負責提供。  
  
### 方法  
 方法的內嵌程式碼不是預設 XAML 功能。  在大部分的情況下，您並不會直接從 XAML 參考方法成員，方法在 XAML 中的角色僅只是為特定的 XAML 模式提供支援。  [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md) 則屬例外。  
  
### 欄位  
 CLR 設計方針不建議使用非靜態欄位。  對於靜態欄位，您只能透過 [x:Static Markup Extension](../../../docs/framework/xaml-services/x-static-markup-extension.md) 存取靜態欄位值；在此情況下，您將無法在 CLR 定義中執行任何特殊作業，以公開 [x:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) 用法的欄位。  
  
## 可附加的成員  
 可附加成員可透過定義型別上的存取子方法模式公開給 XAML。  定義型別本身不一定必須適用於 XAML，才可做為物件。  事實上，常見模式是宣告服務類別，該服務類別的角色是要擁有可附加成員以及實作相關的行為，但不提供任何其他功能 \(如 UI 表示\)。  在以下幾節中，預留位置 *PropertyName* 代表可附加成員的名稱。  該名稱在 [XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md) 中必須是有效的。  
  
 請留意這些模式與型別的其他方法是否會有名稱衝突。  如果有符合其中一個模式的成員存在，該成員可能會被 XAML 處理器解譯成可附加成員用法路徑，即便這不是您的本意。  
  
#### GetPropertyName 存取子  
 `Get` *PropertyName* 存取子的簽章必須是：  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` 物件可在您的實作中指定為更特定的型別。  您可以使用此項目為可附加成員設定用法範圍；超出您預定範圍的用法，將會擲回後續會由 XAML 剖析錯誤揭露的無效轉型例外狀況。  參數名稱 `target` 並非必要項目，但在大部分的實作中會依慣例命名為 `target`。  
  
-   傳回值可指定為實作中的特定型別。  
  
 若要讓具有 <xref:System.ComponentModel.TypeConverter> 功能的文字語法用於可附加成員的屬性中，請將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至 `Get`*PropertyName* 存取子。  套用至 `get` 而非 `set`，可能顯得不夠直接，但此慣例可支援讓唯讀的可附加成員進行序列化的概念，這在使用設計工具時有其效用。  
  
#### SetPropertyName 存取子  
 Set\<*屬性名稱*\> 存取子的簽章必須是：  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` 物件可透過上一節所說明的相同邏輯與結論，在您的實作中指定為更特定的型別。  
  
-   `value` 物件可在您的實作中指定為更特定的型別。  
  
 請記住，此方法的值是來自 XAML 用法的輸入 \(通常採屬性形式\)。  採用屬性形式時，必須有值轉換子可支援文字語法，且您必須設定 `Get`*PropertyName* 存取子的屬性。  
  
### 可附加的成員存放區  
 光是使用存取子方法通常無法將可附加的成員值放入物件圖形中，或從物件圖形中擷取值並正確地予以序列化。  若要提供這個功能，先前存取子簽章中的 `target` 物件必須能夠儲存值。  此儲存機制應與可附加成員準則一致，即成員可附加至該可附加成員不在其成員清單中的目標。  .NET Framework XAML 服務透過 API <xref:System.Xaml.IAttachedPropertyStore> 和 <xref:System.Xaml.AttachablePropertyServices>，提供實作可附加成員存放區的技巧。  <xref:System.Xaml.IAttachedPropertyStore> 會由 XAML 寫入器用來發現存放區實作，而且應實作於存取子的 `target` 設為的型別上。  靜態 <xref:System.Xaml.AttachablePropertyServices> API 是放在存取子的主體內使用，而且是以 <xref:System.Xaml.AttachableMemberIdentifier> 參考可附加的成員。  
  
## XAML 相關 CLR 屬性  
 若要將 XAML 型別系統資訊報告至 .NET Framework XAML 服務，正確設定型別、成員與組件的屬性是很重要的。  無論您預定將型別用於直接以 .NET Framework XAML 服務的 XAML 讀取器與 XAML 寫入器為基礎的 XAML 系統，還是定義或使用採用 XAML、並且以這些 XAML 讀取器與 XAML 寫入器為基礎的架構，都必須正確完成前述設定。  
  
 對於自訂型別的 XAML 支援，如需每個 XAML 相關屬性的清單，請參閱 [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)。  
  
## 使用方式  
 若要使用自訂型別，標記作者必須為包含自訂型別的組件與 CLR 命名空間對應前置詞。  此程序不在本主題的討論之列。  
  
## 存取層級  
 XAML 提供了一種方法來載入和具現化具有 `internal` 存取層級的型別。  提供此功能後，使用者程式碼便可以定義自己的型別，然後具現化來自也是屬於相同使用者程式碼範圍的標記中的類別。  
  
 WPF 中的一個範例是，每當使用者程式碼定義的 <xref:System.Windows.Controls.UserControl> 要預定做為重構 UI 行為的方法，但不要做為任何可能的延伸機制 \(可能透過以 `public` 存取層級宣告支援類別來暗示\) 的一部分。  如果支援程式碼是編譯到將它當成 XAML 型別來參考的相同組件中，即可以 `internal` 存取來宣告此種 <xref:System.Windows.Controls.UserControl>。  
  
 對於在完全信任下載入 XAML 且使用 <xref:System.Xaml.XamlObjectWriter> 的應用程式，永遠會啟用以 `internal` 存取層級載入類別。  
  
 對於在部分信任下載入 XAML 的應用程式，您可以使用 <xref:System.Xaml.Permissions.XamlAccessLevel> API 控制存取層級特性。  另外，延遲機制 \(如 WPF 範本系統\) 必須能夠傳播任何存取層級權限，並保存這些權限到進行最終執行階段評估；這是透過傳遞 <xref:System.Xaml.Permissions.XamlAccessLevel> 資訊在內部處理。  
  
### WPF 實作  
 WPF XAML 使用部分信任存取模型，若是在部分信任下載入 BAML，則對於 BAML 來源組件的存取僅限於 <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>。  在延遲情況下，WPF 使用 <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=fullName> 做為用於傳遞存取層級資訊的機制。  
  
 在 WPF XAML 術語中，「*內部型別*」\(Internal Type\) 是由參考 XAML 所在的同一個組件所定義的型別。  此種型別可以透過 XAML 命名空間來對應，而該 XAML 命名空間刻意省略了對應的 assembly\= 部分，例如，`xmlns:local="clr-namespace:WPFApplication1"`。  如果 BAML 參考內部型別且該型別具有 `internal` 存取層級，這就會為組件產生 `GeneratedInternalTypeHelper` 類別。  如果想要避免 `GeneratedInternalTypeHelper`，您就必須使用 `public` 存取層級，或必須將相關類別併入個別組件中並使該組件變成相依組件。  
  
## 請參閱  
 [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)   
 [XAML Services](../../../docs/framework/xaml-services/index.md)