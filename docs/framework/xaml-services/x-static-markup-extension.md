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
ms.openlocfilehash: 9fa9e51e66af6df4d1a6b1ec94c5010651bbb21d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401510"
---
# <a name="xstatic-markup-extension"></a>x:Static 標記延伸
參考以 Common Language Specification (CLS) 相容的方式定義的任何靜態值程式碼實體。 參考的靜態屬性可在 XAML 中用來提供屬性的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
| | |  
|-|-|  
|`prefix`|選擇性。 參考對應的非預設 XAML 命名空間的前置詞。 `prefix`會在使用方式中明確顯示, 因為您很少會參考來自預設 XAML 命名空間的靜態屬性。 請參閱＜備註＞。|  
|`typeName`|必要項。 定義所需靜態成員的類型名稱。|  
|`staticMemberName`|必要項。 所需靜態值成員的名稱 (常數、靜態屬性、欄位或列舉值)。|  
  
## <a name="remarks"></a>備註  

參考的程式碼實體必須是下列其中一項:  
  
- 常數  
- 靜態屬性  
- 欄位  
- 列舉值

若指定任何其他程式碼實體 (例如非靜態屬性), 則會導致編譯時期錯誤, 如果 XAML 已進行標記編譯, 則為, 否則為 XAML 載入時間剖析例外狀況。  

您可以對`x:Static`目前 xaml 檔的預設 xaml 命名空間中的靜態欄位或屬性進行參考, 不過, 這需要前置詞對應。 XAML 命名空間幾乎一律定義在 XAML 檔的根項目上。  

當使用預設的 XAML 架構內容執行時, 可以 .NET Framework XAML 服務及其 XAML 讀取器和 XAML 寫入器來執行靜態屬性的查閱作業。 此 XAML 架構內容可以使用 CLR 反映, 為物件圖形結構提供必要的靜態值。 您`typeName`所指定的實際上是 XAML 型別名稱, 而不是 CLR 型別名稱, 不過, 在使用預設的 XAML 架構內容時, 或使用所有現有的 CLR 型 XAML 執行架構時, 這些基本上是相同的名稱。  

當您進行的參考`x:Static`不是直接的屬性值類型時, 請務必小心。 在 XAML 處理順序中, 從標記延伸提供的值不會叫用額外的值轉換。 即使您`x:Static`的參考建立文字字串, 而且以文字字串為基礎之屬性值的值轉換通常會針對該特定成員或傳回類型的任何成員值發生, 這是正確的。  

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。  

在技術上, 有兩個其他的 XAML 用法。 不過, 這些使用方式較不常見, 因為它們是不必要的詳細資訊:  

1. 物件元素語法。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. 具有初始化字串之明確成員屬性的屬性語法。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

在 .NET Framework XAML 服務執行中, 此標記延伸模組的處理是由<xref:System.Windows.Markup.StaticExtension>類別所定義。  

`x:Static` 是一種標記延伸。 Xaml 中的`{`所有標記延伸都會在`}`其屬性語法中使用和字元, 這是 xaml 處理器辨識出標記延伸必須提供值的慣例。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 您用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性, 而且大部分有用的靜態屬性都有支援, 例如可在不需要`{x:Static}`的情況下協助使用的型別轉換器。 針對靜態屬性, 如果下列其中一項為真, 您就必須對應 XAML 命名空間的前置詞:  
  
- 您參考的類型存在於 WPF 中, 但不是 WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]) 之預設 XAML 命名空間的一部分。 這是相當常見的使用`x:Static`案例。 例如, 您可以使用`x:Static`參考搭配 XAML 命名空間與<xref:System> CLR 命名空間和 mscorlib 元件的對應, 以便參考<xref:System.Environment>類別的靜態屬性。  
  
- 您正從自訂群組件參考型別。  
  
- 您參考的是存在於 WPF 元件中的類型, 但該類型位於未對應至 WPF 預設 XAML 命名空間一部分的 CLR 命名空間內。 CLR 命名空間與 WPF 預設 XAML 命名空間的對應是由各種 WPF 元件中的定義所執行 (如需此概念的詳細資訊, 請參閱[Xaml 命名空間和 WPF xaml 的命名空間對應](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 如果 CLR 命名空間主要是由通常不是用於 XAML 的類別定義組成, 例如<xref:System.Windows.Threading>, 則非對應的 clr 命名空間可以存在。  
  
 如需如何使用 WPF 前置詞和 XAML 命名空間的詳細資訊, 請參閱[WPF xaml 的 Xaml 命名空間和命名空間對應](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [x:Type 標記延伸模組](x-type-markup-extension.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
