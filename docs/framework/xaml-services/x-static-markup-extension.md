---
title: x:Static 標記延伸
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: eb0c34f259220a0326238b27ab43efd3078b0bcc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207080"
---
# <a name="xstatic-markup-extension"></a>x:Static 標記延伸
參考任何靜態值的程式碼實體中定義[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– 符合規範的方式。 參考的靜態屬性可用來提供的 XAML 中的屬性值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
| | |  
|-|-|  
|`prefix`|選擇性。 是指對應，非預設的 XAML 命名空間前置詞。 `prefix` 會顯示明確使用量因為您很少會參考來自預設 XAML 命名空間的靜態屬性。 請參閱＜備註＞。|  
|`typeName`|必要項。 定義所需的靜態成員的型別名稱。|  
|`staticMemberName`|必要項。 （常數、 靜態屬性、 欄位或列舉值） 所需的靜態值成員的名稱。|  
  
## <a name="remarks"></a>備註  

參考的程式碼實體必須是下列其中一項：  
  
-   常數  
-   靜態屬性  
-   欄位  
-   列舉值

指定任何其他程式碼實體，例如非靜態屬性，會導致編譯時期錯誤，如果 XAML 標記編譯或 XAML 載入時間剖析例外狀況。  

您可以進行`x:Static`靜態欄位或屬性不在目前的 XAML 文件; 的預設 XAML 命名空間中的參考不過，這需要前置詞對應。 XAML 命名空間幾乎一定會定義在 XAML 文件的根項目。  

靜態屬性的查閱作業可以執行由.NET Framework XAML 服務及其 XAML 讀取器和 XAML 寫入器，在執行時都會使用預設 XAML 結構描述內容。 此 XAML 結構描述內容可用於 CLR 反映提供的物件圖形建構必要的靜態值。 `typeName`您指定實際上是 XAML 型別名稱，不是 CLR 型別名稱，不過這些是基本上相同的名稱，或使用所有現有的 CLR 為基礎 XAML 實作架構時使用的預設 XAML 結構描述內容。  

當您進行時請特別小心`x:Static`不直接是屬性的值類型的參考。 在 XAML 中處理順序，提供來自標記延伸的值不會叫用其他的值轉換。 也是如此即使您`x:Static`參考建立文字字串，並針對該特定成員或傳回型別的任何成員值，就會發生值的轉換通常根據文字字串的屬性值。  

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。  

有兩個其他在技術上可行的 XAML 用法。 不過，這些使用方式是較不常見，因為它們是必要的詳細資訊：  

1.  物件元素語法。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  屬性使用明確的成員屬性，初始化字串的語法。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.StaticExtension>類別。  

`x:Static` 是標記延伸。 在 XAML 使用的所有標記延伸`{`和`}`字元在其屬性語法中，這是用 XAML 處理器會辨識為標記延伸必須提供值的慣例。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 您用於 WPF 程式設計的預設 XAML 命名空間不包含許多實用的靜態屬性，且大部分的有用的靜態屬性都有支援，像是可簡化使用方式，而不需要型別轉換子`{x:Static}`。 靜態屬性，您必須對應 XAML 命名空間的前置詞，如果下列其中一項為真：  
  
-   您要參考存在於 WPF，但不是 WPF 預設 XAML 命名空間的一部分的型別 ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)])。 這是很常見的案例，使用`x:Static`。 例如，您可以使用`x:Static`XAML 命名空間對應至參考<xref:System>若要參考的靜態屬性的 CLR 命名空間和 mscorlib 組件<xref:System.Environment>類別。  
  
-   您從自訂組件參考的型別。  
  
-   但是該類型是 CLR 命名空間的未對應到屬於 WPF 預設 XAML 命名空間內，您要參考存在於 WPF 組件的類型。 所對應的 CLR 命名空間至預設 XAML 命名空間的 WPF 藉由各種不同的 WPF 組件中的定義 (如需有關這個概念的詳細資訊，請參閱 < [XAML 命名空間和 WPF XAML 命名空間對應](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 如果該 CLR 命名空間包含大部分的類別定義，通常不適用於 XAML，這類非對應的 CLR 命名空間中可以存在<xref:System.Windows.Threading>。  
  
 如需有關如何使用 wpf 的前置詞和 XAML 命名空間的詳細資訊，請參閱 < [XAML 命名空間和命名空間對應 WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [x:Type 標記延伸](x-type-markup-extension.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
