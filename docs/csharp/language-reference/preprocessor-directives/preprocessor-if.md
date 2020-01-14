---
title: '#if 前置處理器指示詞 - C# 參考'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899846"
---
# <a name="if-c-reference"></a>#if （C#參考）

當 C# 編譯器遇到 `#if` 指示詞，且其後接著 [#endif](preprocessor-endif.md) 指示詞時，只有在定義了指定的符號時，它才會編譯指示詞之間的程式碼。 不同於 C 和 C++，您無法將數值指派給符號。 中C#的 `#if` 語句是布林值，而且只會測試是否已定義符號。 例如：

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

您只能使用運算子[==](../operators/equality-operators.md#equality-operator-) （相等）和[！ =](../operators/equality-operators.md#inequality-operator-) （不等）來測試 `true` 或 `false`的[bool](../builtin-types/bool.md)值。 `true` 表示已定義符號。 `#if DEBUG` 陳述式的意義與 `#if (DEBUG == true)` 一樣。 您可以使用[& & （和）](../operators/boolean-logical-operators.md#conditional-logical-and-operator-)、 [ &#124; &#124; （或）](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)和[！（不是）](../operators/boolean-logical-operators.md#logical-negation-operator-)用來評估是否已定義多個符號的運算子。 您也可以使用括弧來將符號和運算子分組。

## <a name="remarks"></a>備註

`#if` 連同 [#else](preprocessor-else.md)、[#elif](preprocessor-elif.md)、[#endif](preprocessor-endif.md)、[#define](preprocessor-define.md) 及 [#undef](preprocessor-undef.md) 指示詞，可讓您根據一或多個符號是否存在來包含或排除程式碼。 在編譯偵錯組建的程式碼時，或是在針對特定組態進行編譯時，這非常實用。

以 `#if` 指示詞開頭的條件式指示詞必須明確地以 `#endif` 指示詞終止。

`#define` 可讓您定義符號。 屆時，使用該符號作為傳遞到 `#if` 指示詞的運算式，運算式就會評估為 `true`。

您也可以使用 [-define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。 您可以使用 [#undef](preprocessor-undef.md) 來取消定義符號。

透過 `-define` 或 `#define` 定義的符號不會與相同名稱的變數發生衝突。 也就是說，您不應將變數名稱傳遞給前置處理器指示詞，而且符號僅能由前置處理器指示詞來評估。

使用 `#define` 建立的符號範圍是定義它的檔案。

組建系統也會留意代表 SDK 樣式專案中不同[目標 framework](../../../standard/frameworks.md)的預先定義預處理器符號。 若要建立能以多個 .NET 實作或版本為目標的應用程式，這些符號就很實用。

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> 針對傳統 .NET Framework 專案，您必須透過專案的 [屬性] 頁面，手動設定 Visual Studio 中不同目標 framework 的條件式編譯符號。

其他預先定義符號包括 DEBUG 和 TRACE 常數。 您可以使用 `#define` 來覆寫為專案所設定的值。 例如，DEBUG 符號會根據您的組建組態屬性 ("Debug" 或 "Release" 模式) 而自動設定。

## <a name="examples"></a>範例

以下範例說明如何在檔案上定義 MYTEST 符號，然後測試 MYTEST 和 DEBUG 符號的值。 此範例的輸出視您使用 Debug 或 Release 組態模式建置專案而有所不同。

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

以下範例說明如何測試不同的目標 Framework，讓您可以盡可能使用較新的 API：

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](index.md)
- [如何：使用追蹤和偵錯進行條件式編譯](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
