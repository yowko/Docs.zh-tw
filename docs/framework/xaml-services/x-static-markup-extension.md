---
title: "x:Static 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 647bfed7b321a949090f6da047f9b8105d335101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xstatic-markup-extension"></a>x:Static 標記延伸
參考任何靜態值的程式碼實體中定義[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– 相容的方式。 參考的靜態屬性可以用來提供屬性，以在 XAML 中的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`prefix`|選擇性。 是指對應、 非預設 XAML 命名空間前置詞。 `prefix`顯示明確使用因為您很少會參考來自預設 XAML 命名空間的靜態屬性。 請參閱＜備註＞。|  
|`typeName`|必要。 定義所需的靜態成員的型別名稱。|  
|`staticMemberName`|必要。 （常數、 靜態屬性、 欄位或列舉值） 所需的靜態值成員的名稱。|  
  
## <a name="remarks"></a>備註  
 參考的程式碼實體必須是下列其中一項：  
  
-   常數  
  
-   靜態屬性  
  
-   欄位  
  
-   列舉值  
  
 指定任何其他程式碼的實體，例如非靜態屬性，會導致編譯時期錯誤，如果在 XAML 標記編譯或 XAML 的載入時間分析例外狀況。  
  
 您可以進行`x:Static`參考靜態欄位或屬性不在目前的 XAML 文件; 的預設 XAML 命名空間，然而，您需要的前置詞對應。 XAML 命名空間幾乎一定會定義在 XAML 文件的根項目。  
  
 靜態屬性的查閱作業只能由.NET Framework XAML 服務和 XAML 讀取器和 XAML 寫入器，在執行時都會與預設 XAML 結構描述內容。 此 XAML 結構描述內容可以使用 CLR 反映提供的物件圖形建構必要的靜態值。 `typeName`您指定實際上是 XAML 型別名稱，不是 CLR 型別名稱，雖然這些是基本上相同的名稱，或使用所有現有以 CLR 為基礎實作 XAML 的架構時使用的預設 XAML 結構描述內容。  
  
 當您進行時請特別小心`x:Static`參考不會直接是屬性值的型別。 在 XAML 中處理順序，提供從標記延伸的值不會叫用其他值的轉換。 也是如此即使您`x:Static`參考建立文字字串，並針對該特定成員或成員的任何值傳回型別，就會發生值的轉換通常根據文字字串的屬性值。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。  
  
 有兩個其他是可行的 XAML 用法。 不過，這些使用方式的較不常見，因為它們是必要的詳細資訊：  
  
 **物件項目語法：** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`  
  
 **屬性具有明確的初始化字串的成員屬性的語法：** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`  
  
 在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.StaticExtension>類別。  
  
 `x:Static` 是一種標記延伸。 所有標記延伸在 XAML 使用`{`和`}`字元在其屬性語法中，也就是，XAML 處理器會辨識標記延伸必須提供值的慣例。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 您使用 WPF 程式設計的預設 XAML 命名空間不包含許多實用的靜態屬性，而且大部分的有用的靜態屬性會有支援，例如類型轉換器，以便使用方式，而不需要`{x:Static}`。 靜態屬性，您必須對應 XAML 命名空間前置詞，如果下列其中一項成立：  
  
-   您所參考的類型存在於 WPF 中，但不是 WPF 的預設 XAML 命名空間的一部分 ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)])。 這是很常見的案例使用`x:Static`。 例如，您可能會使用`x:Static`XAML 命名空間對應至參考<xref:System>CLR 命名空間和 mscorlib 組件參考的靜態屬性才能<xref:System.Environment>類別。  
  
-   您從自訂組件參考類型。  
  
-   但該型別是 WPF 預設 XAML 命名空間的一部分未對應的 CLR 命名空間內參考存在於 WPF 組件的類型。 定義各種不同的 WPF 組件中所執行之 CLR 命名空間可到預設 XAML 命名空間對應 wpf (如需有關這個概念的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 如果大部分的類別定義通常不適用於 XAML 中，例如組成該 CLR 命名空間，可以存在非對應的 CLR 命名空間<xref:System.Windows.Threading>。  
  
 如需有關如何使用前置詞和 XAML 命名空間的 WPF 的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
## <a name="see-also"></a>請參閱  
 [x:Type 標記延伸模組](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [從 WPF 移轉至 System.Xaml 的類型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
