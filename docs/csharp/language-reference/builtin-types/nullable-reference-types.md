---
title: 空白參考型態 - C# 參考
description: 瞭解 C# 可空參考型態以及如何使用它們
ms.date: 04/06/2020
ms.openlocfilehash: cbc7397ac76b43b79a4168f4c61fe2c631b4a46b
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888313"
---
# <a name="nullable-reference-types-c-reference"></a>空白引言型態 (C# 引用)

> [!NOTE]
> 本文介紹可無效的引用類型。 您可以宣告[空數型態](nullable-value-types.md)。

空引用類型從 C# 8.0 開始可用,在已選擇輸入*空感知上下文*的代碼中。 空引用類型、空靜態分析警告和[允許無效運算符](../operators/null-forgiving.md)是可選的語言功能。 默認情況下,所有功能都處於關閉狀態。 在專案等級使用產生設定或在使用實用機制的代碼中控制*可無效上下文*。

 在可復原的感知的文字中:

- 引用類型的`T`變數必須用非 null 初始化,並且可能永遠不會分配可能`null`為的值。
- 引用類型的`T?`變數可以使用`null`初始化或`null`分配 ,但在取消引用之前`null`需要針對 它進行檢查。
- 在應用`m`null`T?`寬容運算符(如中`m!`)時,類型的變數被視為非 null。

非可引用類型和空引用類型`T``T?`之間的區別由編譯器對上述規則的解釋強制執行。 類型的`T`變數和類型的`T?`變數由相同的 .NET 類型表示。 以下範例宣告一個不可否定的字串和一個空字串,然後使用 null 寬容運算元將值分配給不可否定的字串:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

變數`notNull`和`nullable`變數都由<xref:System.String>類型表示。 由於不可取消和可 null 的類型都儲存為同一類型,因此不允許使用空引用類型。 通常,空引用類型不能用作基類或實現的介面。 任何物件創建或類型測試表達式都不能使用空引用類型。 空引用類型不能是成員訪問表達式的類型。 以下範例顯示以下建構:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>可空參考與靜態分析

上一節中的示例說明了可空引用類型的性質。 空引用類型不是新的類類型,而是對現有引用類型的註釋。 編譯器使用這些註釋來説明您在代碼中找到潛在的空引用錯誤。 不可取消的引用類型和空引用類型之間沒有運行時差異。 編譯器不添加任何非空引用類型的運行時檢查。 好處是在編譯時間分析。 編譯器會生成警告,以説明您尋找和修復程式碼中的潛在空錯誤。 聲明您的意圖,當代碼違反該意圖時,編譯器會發出警告。

在啟用的可啟用的上下文中,編譯器對任何引用類型的變數執行靜態分析,這些變數都是空的和不可否定的。 編譯器將每個引用變數的 null 狀態追蹤為*不為 null*或*可能為 null*。 無法空引的預設狀態*為 null*。 空引言的預設狀態*可能為 null*。

無法空的引用類型應始終安全取消引用,因為它們的 null 狀態不是*null*。 要強制執行該規則,如果非空引用類型未初始化為非 null 值,編譯器將發出警告。 必須將局部變數指定在聲明位置。 每個構造函數必須分配每個欄位,無論是在其正文中,還是調用構造函數,要麼使用欄位初始化器。 如果將不可取消的引用分配給狀態*可能為空*的引用,編譯器將發出警告。 但是,由於不可空引用*不為空*,因此當取消引用這些變數時,不會發出警告。

可空引為型態可以初始化或`null`分配給 。 因此,靜態分析必須在取消引用變數之前確定變數*不是 null。* 如果確定可空引用*為空*,則無法將其分配給不可取消的引用變數。 以下類別顯示了這些警告的範例:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

以下代碼片段顯示編譯器在使用此類時發出警告的位置:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

前面的範例演示了編譯器的靜態分析,以確定引用變數的 null 狀態。 編譯器對空檢查和賦值應用語言規則來通知其分析。  編譯器不能對方法或屬性的語義進行假設。 如果調用執行空檢查的方法,編譯器無法知道這些方法會影響變數的 null 狀態。 有許多屬性可以添加到 API 中,以便通知編譯器參數和返回值的語義。 這些屬性已應用於 .NET 核心庫中的許多常見 API。 例如,<xref:System.String.IsNullOrEmpty%2A>已更新,編譯器將該方法正確解釋為空檢查。 有關應用於空狀態靜態分析的屬性的詳細資訊,請參閱關於[null 可屬性](../../nullable-attributes.md)的文章。

## <a name="setting-the-nullable-context"></a>設定可無效的內容

有兩種方法可以控制可無效上下文。 在項目級別,可以添加`<Nullable>enable</Nullable>`專案設置。 在單個 C# 源檔案中,`#nullable enable`可以新增雜注以啟用可 null 上下文。 請參閱有關[設置空策略](../../nullable-attributes.md)的文章。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊,請參閱[以下 C# 語言規範](~/_csharplang/spec/introduction.md)的建議:

- [可為 Null 的參考型別](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [草稿空參考類型規範](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [可為 Null 的實值型別](nullable-value-types.md)
