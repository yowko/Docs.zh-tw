---
title: '可為 null 的參考型別-c # 參考'
description: '深入瞭解 c # 可為 null 的參考型別，以及如何使用它們'
ms.date: 04/06/2020
ms.openlocfilehash: 274a613a8381a2b7718c9025f51aadb2eb32af36
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471859"
---
# <a name="nullable-reference-types-c-reference"></a>可為 null 的參考型別 (c # 參考) 

> [!NOTE]
> 本文涵蓋可為 null 的參考型別。 您也可以宣告 [可為 null 的實數值型別](nullable-value-types.md)。

從 c # 8.0 開始，可為 null 的參考型別（在已加入 *可為 null 感知內容*的程式碼中）。 可為 null 的參考型別、null 靜態分析警告和 [null 容許運算子](../operators/null-forgiving.md) 是選擇性的語言功能。 預設會關閉所有。 *可為 null 的內容*可在專案層級使用組建設定或使用 pragma 的程式碼來控制。

 在可為 null 的感知內容中：

- 參考型別的變數 `T` 必須使用非 null 來初始化，而且可能永遠不會指派可能的值 `null` 。
- 參考型別的變數 `T?` 可能會使用 `null` 或指派 `null` ，但在取消參考之前必須先進行檢查 `null` 。
- `m` `T?` 當您套用 null 容許運算子時，型別的變數會被視為非 null，如下所示 `m!` 。

不可為 null 的參考型別 `T` 與可為 null 的參考型別之間的差異， `T?` 是由編譯器對上述規則的解讀來強制執行。 型別的變數 `T` 和型別的變數， `T?` 是以相同的 .net 型別表示。 下列範例會宣告不可為 null 的字串與可為 null 的字串，然後使用 null 容許運算子將值指派給不可為 null 的字串：

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

變數 `notNull` 和 `nullable` 都是由型別表示 <xref:System.String> 。 因為不可為 null 且可為 null 的型別同時儲存為相同類型，所以不允許使用可為 null 的參考型別的數個位置。 一般而言，可為 null 的參考型別不能當做基類或實介面使用。 可為 null 的參考型別不能用在任何物件建立或型別測試運算式中。 可為 null 的參考型別不能是成員存取運算式的類型。 下列範例會顯示這些結構：

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

## <a name="nullable-references-and-static-analysis"></a>可為 null 的參考和靜態分析

上一節中的範例說明可為 null 的參考型別的本質。 可為 null 的參考型別不是新的類別型別，而是現有參考型別的批註。 編譯器會使用這些注釋來協助您在程式碼中找出潛在的 null 參考錯誤。 不可為 null 的參考型別與可為 null 的參考型別之間沒有任何執行時間差異。 編譯器不會為不可為 null 的參考型別新增任何執行時間檢查。 這些優點是在編譯時期分析中。 編譯器會產生警告，協助您找出並修正程式碼中的潛在 null 錯誤。 您可以宣告您的意圖，而編譯器會在您的程式碼違反該意圖時警告您。

在可為 null 的啟用內容中，編譯器會在任何參考型別的變數上執行靜態分析，可為 null 且不可為 null。 編譯器會將每個參考變數的 null 狀態追蹤為 *非 null* 或 *可能是 null*。 不可為 null 參考的預設狀態 *不是 null*。 可為 null 參考的預設狀態 *可能是 null*。

不可為 null 的參考型別應該一律安全地進行取值，因為它們的 null 狀態 *不是 null*。 若要強制執行該規則，如果不可為 null 的參考型別未初始化為非 null 值，則編譯器會發出警告。 區域變數必須在宣告時指派。 每個函式都必須在其主體、呼叫的函式或使用欄位初始化運算式中，指派每個欄位。 如果不可為 null 的參考指派給其狀態 *可能是 null*的參考，則編譯器會發出警告。 不過，因為不可為 null 的參考不是 *null*，所以當這些變數被解除參考時，不會發出任何警告。

可為 null 的參考型別可以初始化或指派給 `null` 。 因此，靜態分析必須在取值之前判斷變數 *不是 null* 。 如果可為 null 的參考判斷為 *null*，則無法將它指派給不可為 null 的參考變數。 下列類別會顯示這些警告的範例：

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

下列程式碼片段顯示使用這個類別時，編譯器發出警告的位置：

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

上述範例示範編譯器的靜態分析，以判斷參考變數的 null 狀態。 編譯器會針對 null 檢查和指派套用語言規則，以通知其分析。  編譯器無法對方法或屬性的語義進行假設。 如果您呼叫的方法會執行 null 檢查，則編譯器無法得知這些方法會影響變數的 null 狀態。 您可以新增多個屬性給 Api，以通知編譯器有關引數和傳回值的語法。 這些屬性已套用至 .NET Core 程式庫中的許多常見 Api。 例如，已 <xref:System.String.IsNullOrEmpty%2A> 更新，且編譯器會將該方法正確地解讀為 null 檢查。 如需適用于 null 狀態靜態分析之屬性的詳細資訊，請參閱 [可為 null 屬性](../attributes/nullable-analysis.md)的相關文章。

## <a name="setting-the-nullable-context"></a>設定可為 null 的內容

有兩種方式可控制可為 null 的內容。 在專案層級，您可以加入 `<Nullable>enable</Nullable>` 專案設定。 在單一 c # 原始檔中，您可以加入 `#nullable enable` pragma 來啟用可為 null 的內容。 請參閱 [設定可為 null 策略](../../nullable-migration-strategies.md)的文章。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱下列 [c # 語言規格](~/_csharplang/spec/introduction.md)提案：

- [可為 Null 的參考型別](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [草稿可為 null 的參考型別規格](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [可為 null 的實數值型別](nullable-value-types.md)
