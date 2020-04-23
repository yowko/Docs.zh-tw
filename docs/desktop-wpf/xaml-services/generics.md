---
title: XAML 中的泛型
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071735"
---
# <a name="generics-in-xaml"></a>XAML 中的泛型

.NET XAML<xref:System.Xaml?displayProperty=fullName>服務( 如實現)支援使用通用 CLR 類型。 此支援包括指定泛型的約束作為類型參數,並通過調用泛型集合案例的適當`Add`方法來強制執行約束。 本主題介紹在 XAML 中使用和引用泛型類型的方面。

## <a name="xtypearguments"></a>x:類型參數

`x:TypeArguments`是由 XAML 語言定義的指令。 當它用作由泛型類型支援的 XAML 類型的成員`x:TypeArguments`時, 將泛型的約束類型參數傳遞給支援構造函數。 有關 與 .NET XAML`x:TypeArguments`服務使用 相關的引用語法,其中包括語法範例,請參閱[x:TypeArguments 指令](xtypearguments-directive.md)。

由於`x:TypeArguments`採用字串,並且具有類型轉換器支援,因此通常在 XAML 用法中聲明為屬性。

在 XAML 節點流中,可以`x:TypeArguments`從節點`StartObject`流<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>中 的位置獲取聲明的資訊。 的傳回<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>值 是值<xref:System.Xaml.XamlType>的清單 。 可以通過調<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>用 確定 XAML 類型是否表示泛型類型。

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>XAML 中泛型的規則和語法約定

在 XAML 中,泛型類型必須始終表示為受約束的泛型。 無約束泛型永遠不會存在於 XAML 類型系統或 XAML 節點流中,並且不能在 XAML 標記中表示。 泛型可以在 XAML 屬性語法中引用,用於對於泛型`x:TypeArguments`是 被引用的泛型的嵌套類型約束的情況`x:Type`,或者對於為泛型類型提供 CLR 類型引用的情況。 通過 .NET XAML<xref:System.Xaml.Schema.XamlTypeTypeConverter>服務定義的類支援引用泛型。

XAML 屬性語法窗體<xref:System.Xaml.Schema.XamlTypeTypeConverter>通過 更改典型的 MSIL/ CLR 語法約定而啟用,該約定使用角度括弧來表示泛型的類型和約束,而是替換約束容器的括弧。 例如,請參閱[x:Type 參數指令](xtypearguments-directive.md)。

## <a name="generics-and-xaml-2009-features"></a>泛型和 XAML 2009 功能

如果使用 XAML 2009 而不是映射 CLR 基類型以獲取通用語言基元中的 XAML 類型,則可以使用[XAML 2009 內置類型](types-for-primitives.md)作為中的`x:TypeArguments`資訊項。 例如,您可以聲明以下內容(未顯示前置碼映射,但`x`XAML 語言 XAML 2009 的命名空間):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>WPF 中的統般支援

對於專門針對 WPF 的 XAML 2006 用法,x:class 還必須[x:Class](xclass-directive.md)提供`x:TypeArguments`與的元素,並且該元素必須是 XAML 文件中的根元素。 根元素必須映射到具有至少一個類型參數的泛型類型。 例如 <xref:System.Windows.Navigation.PageFunction%601>。

支援泛型用法的可能解決方法包括定義可以返回泛型類型的自定義標記擴展,或提供從泛型類型派生但在其自己的類定義中平展泛型約束的換行類定義。

在 WPF 中,您可以將 XAML 2009`x:TypeArguments`功能與 一起使用 ,但僅適用於鬆散的 XAML(未標記編譯的 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。

.NET 框架 3.5 的 Windows 工作流基礎中的自定義工作流不支援通用的 XAML 使用。

## <a name="see-also"></a>另請參閱

- [x:TypeArguments 指示詞](xtypearguments-directive.md)
- [x:Class 指示詞](xclass-directive.md)
- [通用 XAML 語言基本類型的內建類型](types-for-primitives.md)
