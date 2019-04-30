---
title: XAML 中的泛型
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9263edf18872f510f5f2f4e3e9cb793e45c5d0b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954098"
---
# <a name="generics-in-xaml"></a>XAML 中的泛型
.NET Framework XAML 服務中 System.Xaml 實作提供支援使用泛型的 CLR 型別。 這項支援包括作為類型引數中指定的泛型條件約束，並強制執行條件約束，藉由呼叫適當`Add`泛型集合案例的方法。 本主題描述使用和參考 XAML 中的泛型類型的層面。  
  
## <a name="xtypearguments"></a>x:TypeArguments  
 `x:TypeArguments` XAML 語言所定義的指示詞。 使用泛型型別，做為後盾的 XAML 型別成員時`x:TypeArguments`類型的泛型支援建構函式的引數傳遞限制。 如需有關.NET Framework XAML 服務的參考語法中，使用的`x:TypeArguments`，包括語法範例，請參閱[X:typearguments 指示詞](x-typearguments-directive.md)。  
  
 因為`x:TypeArguments`採用字串，並具有型別轉換子支援，它通常會在 XAML 做為屬性的使用方式中宣告。  
  
 XAML 節點資料流中的資訊則是由宣告`x:TypeArguments`可以取自<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>在`StartObject`節點資料流中的位置。 傳回值<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>是一份<xref:System.Xaml.XamlType>值。 藉由呼叫進行的 XAML 型別是否代表泛型型別判斷<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>。  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>規則和 XAML 的泛用的語法慣例  
 在 XAML 中，泛型型別必須一律會顯示為受條件約束的泛型;未受限制的泛型永遠不會存在於 XAML 類型系統或 XAML 節點資料流，而無法表示在 XAML 標記中。 泛型可參考的情況下，很巢狀的類型條件約束的泛型所參考的 XAML 屬性語法內`x:TypeArguments`，或者是其中`x:Type`提供泛型型別的 CLR 型別參考。 這透過支援<xref:System.Xaml.Schema.XamlTypeTypeConverter>.NET Framework XAML 服務所定義的類別。  
  
 XAML 屬性語法形式啟用<xref:System.Xaml.Schema.XamlTypeTypeConverter>改變典型的 MSIL / CLR 語法慣例，會使用角括號的類型和條件約束的泛型，並改為換成條件約束的容器的括號。 如需範例，請參閱[X:typearguments 指示詞](x-typearguments-directive.md)。  
  
## <a name="generics-and-xaml-2009-features"></a>泛型和 XAML 2009 功能  
 如果您使用 XAML 2009 而不是將 CLR 對應基底型別，以取得通用語言基本類型的 XAML 型別，您可以使用[XAML 2009 的內建型別](built-in-types-for-common-xaml-language-primitives.md)中的資訊項目`x:TypeArguments`。 例如，您可以宣告下列 (前置詞對應不會顯示，但`x`是 XAML 2009 的 XAML 語言 XAML 命名空間):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF 和其他 v3.5 架構中的泛型支援  
 特別以 WPF 為目標時，XAML 2006 使用量[X:class](x-class-directive.md)也必須提供相同的項目，做為`x:TypeArguments`，且該項目必須是在 XAML 文件中的根項目。 根項目必須對應到至少一個類型引數的泛型型別。 例如， <xref:System.Windows.Navigation.PageFunction%601>。  
  
 可能的因應措施，以支援一般用法包括定義自訂標記延伸可傳回泛型型別，或提供換行類別衍生自泛型型別，但將在其自己的類別定義中的泛型條件約束的定義。  
  
 在 WPF 與目標[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，您可以使用 XAML 2009 功能，並搭配`x:TypeArguments`，但只在鬆散的 XAML (未標記編譯的 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 針對 Windows Workflow Foundation 中的自訂工作流程[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]不支援一般的 XAML 用途。  
  
## <a name="see-also"></a>另請參閱

- [x:TypeArguments 指示詞](x-typearguments-directive.md)
- [x:Class 指示詞](x-class-directive.md)
- [通用 XAML 語言基本類型的內建類型](built-in-types-for-common-xaml-language-primitives.md)
