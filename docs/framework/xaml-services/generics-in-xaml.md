---
title: XAML 中的泛型
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: faef74c57ac5ff9e3d4162accfc6552db55715bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="generics-in-xaml"></a>XAML 中的泛型
.NET Framework XAML 服務實作於 System.Xaml 中提供支援使用泛型的 CLR 型別。 這項支援包括指定的條件約束的泛型型別引數，並強制執行條件約束，藉由呼叫適當`Add`泛型集合的情況下的方法。 本主題描述使用，並參考 XAML 中的泛型類型的層面。  
  
## <a name="xtypearguments"></a>x: TypeArguments  
 `x:TypeArguments` XAML 語言所定義的指示詞。 使用泛型類型，支援將 XAML 類型的成員時`x:TypeArguments`類型引數的泛型支援建構函式的條件約束的傳遞。 適用於.NET Framework XAML 服務的參考語法使用`x:TypeArguments`，其中包括語法範例，請參閱[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。  
  
 因為`x:TypeArguments`取用一個字串，且具有類型轉換子的支援，它通常在做為屬性的 XAML 用法中宣告。  
  
 XAML 節點資料流中的資訊則是由宣告`x:TypeArguments`可以取自<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>在`StartObject`節點資料流中的位置。 傳回值<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>是一份<xref:System.Xaml.XamlType>值。 判斷 XAML 型別是否代表泛型型別可透過呼叫<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>。  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>規則和 XAML 的泛用的語法慣例  
 在 XAML 中，泛型型別必須永遠會表示為受條件約束的泛型;受條件約束的泛型永遠不會在 XAML 類型系統或 XAML 節點資料流中且無法在 XAML 標記中。 XAML 屬性語法的情況，它所參考的泛型的巢狀的類型條件約束內可以參考泛型`x:TypeArguments`，或者是其中`x:Type`提供泛型型別的 CLR 型別參考。 這透過支援<xref:System.Xaml.Schema.XamlTypeTypeConverter>.NET Framework XAML 服務所定義的類別。  
  
 XAML 屬性語法形式啟用<xref:System.Xaml.Schema.XamlTypeTypeConverter>改變一般 MSIL CLR 語法慣例，會使用角括號的類型和條件約束的泛型，並改為替代條件約束的容器的括號。 如需範例，請參閱[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。  
  
## <a name="generics-and-xaml-2009-features"></a>泛型和 XAML 2009 功能  
 如果您使用 XAML 2009 而不是將 CLR 對應基底類型，以取得通用語言基本類型的 XAML 型別，您可以使用[XAML 2009 的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)為中的資訊項目`x:TypeArguments`。 例如，您可以宣告下列 (前置詞對應不會顯示，但`x`是 XAML 2009 的 XAML 語言 XAML 命名空間):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF 和其他 v3.5 架構中的泛型支援  
 特別以 WPF 為目標時，XAML 2006 使用量[X:class](../../../docs/framework/xaml-services/x-class-directive.md)也必須在相同的項目，做為提供`x:TypeArguments`，與該項目必須是 XAML 文件中的根項目。 根項目必須具有至少一個型別引數的泛型型別對應。 範例是<xref:System.Windows.Navigation.PageFunction%601>。  
  
 可能的因應措施，以支援一般用法包括定義自訂標記延伸可傳回泛型型別，或提供換行類別衍生自泛型型別，但將在類別定義中的泛型條件約束的定義。  
  
 在 WPF 和目標[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，您可以使用 XAML 2009 功能與搭配`x:TypeArguments`，但僅針對鬆散的 XAML (未標記編譯 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 自訂工作流程中的 Windows Workflow Foundation[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]不支援泛型的 XAML 用法。  
  
## <a name="see-also"></a>另請參閱  
 [x:TypeArguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [通用 XAML 語言基本類型的內建類型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
