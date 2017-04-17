---
title: "x:Static Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticExtension"
  - "xStatic"
  - "x:Static"
helpviewer_keywords: 
  - "x:Static markup extension [XAML Services]"
  - "Static markup extension in XAML [XAML Services]"
  - "XAML [XAML Services], x:Static markup extension"
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: 25
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 25
---
# x:Static Markup Extension
參考以與 [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] 相容的方式定義之任何靜態值程式碼實體。  參考的靜態屬性可以用來提供 XAML 中的屬性值。  
  
## XAML Attribute Usage  
  
```  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`prefix`|選擇項。  參考至對應、非預設之 XAML 命名空間的前置詞。  `prefix` 以此使用方式明確地顯示，這是因為您很少會參考來自預設 XAML 命名空間的靜態屬性。  請參閱＜備註＞。|  
|`typeName`|必要項。  定義所需靜態成員之型別的名稱。|  
|`staticMemberName`|必要項。  所需靜態值成員的名稱 \(常數、靜態屬性、欄位或列舉值\)。|  
  
## 備註  
 參考的程式碼實體必須是下列其中一項：  
  
-   常數  
  
-   靜態屬性  
  
-   欄位  
  
-   列舉值  
  
 指定其他任何程式碼實體，例如非靜態屬性，會造成 XAML 進行標記編譯時的編譯錯誤，或是 XAML 載入時間例外狀況。  
  
 您可以建立 `x:Static` 參考，這個參考的對象可以是不在目前 XAML 文件之預設 XAML 命名空間內的靜態欄位或屬性，但是這樣需要前置詞對應。  XAML 命名空間幾乎永遠都會在 XAML 文件的根項目上定義。  
  
 在以預設 XAML 結構描述內容執行時，靜態屬性的查閱作業，可以由 .NET Framework XAML Services 及其 XAML 讀取器和 XAML 寫入器來執行。  此 XAML 結構描述內容可使用 CLR 反映來提供物件圖形建構必要的靜態值。  您指定的 `typeName` 實際上是 XAML 型別名稱，而不是 CLR 型別名稱，儘管在使用預設 XAML 結構描述內容時，或在使用所有現有基於 CLR 的 XAML 實作架構時，這些名稱基本上都相同。  
  
 建立不是屬性值直接型別的 `x:Static` 參考時，請小心進行。  在 XAML 處理序列中，提供標記延伸中的值不會叫用其他的值轉換。  即使您的 `x:Static` 參考會造成文字字串，而且通常會針對該特定成員或傳回型別的任何成員值，發生根據文字字串的屬性值的值轉換，也依然是如此。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `x:Static` 識別項字串後提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension> 延伸類別的 <xref:System.Windows.Markup.StaticExtension.Member%2A> 值。  
  
 有兩個技術上可能的其他 XAML 使用方式。  不過，這些使用方式較不常見，因為它們具有不必要地詳細資訊：  
  
 **物件項目語法**：`<x:Static Member="``prefix``:``typeName``.``staticMemberName``" .../>`  
  
 **初始化字串之運用明確成員屬性 \(Property\) 的屬性 \(Attribute\) 語法**：`<``object````property``="{x:Static Member=``prefix``:``typeName``.``staticMemberName``}" .../>`  
  
 在 .NET Framework XAML Services 實作中，此標記延伸的處理是由 <xref:System.Windows.Markup.StaticExtension> 類別所定義。  
  
 `x:Static` 是一種標記延伸。  XAML 中的所有標記延伸都會在其屬性 \(Attribute\) 語法中使用 `{` 與 `}` 字元，此慣例讓 XAML 處理器知道某個標記延伸必須提供值。  如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
## WPF 使用注意事項  
 您要用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性，大多數有用的靜態屬性都有型別轉換子之類的支援，可便於使用而不需要 `{x:Static}`。  對於靜態屬性，如果下列其中一項成立，您就必須對應 XAML 命名空間的前置詞：  
  
-   您所參考的型別存在於 WPF 中，但不是 WPF \([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]\) 之預設 XAML 命名空間的一部分。  這是使用 `x:Static` 的常見情形。  例如，您可能會使用 `x:Static` 參考，運用對應至 <xref:System> CLR 命名空間和 mscorlib 組件的 XAML 命名空間對應，以參考 <xref:System.Environment> 類別的靜態屬性。  
  
-   您從自訂組件 \(Assembly\) 參考型別。  
  
-   您參考存在於 WPF 組件中的型別，但該型別位於 CLR 命名空間內，而此命名空間未對應為 WPF 預設 XAML 命名空間的一部分。  CLR 命名空間到 WPF 預設 XAML 命名空間的對應是由不同 WPF 組件中的定義所執行 \(如需此概念的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../ocs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)\)。  如果 CLR 命名空間的絕大部分都由通常不為 XAML 所用的類別定義組成，例如 <xref:System.Windows.Threading>，就不能存在非對應的 CLR 命名空間。  
  
 如需如何使用 WPF 之前置詞和 XAML 命名空間的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../ocs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
## 請參閱  
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)