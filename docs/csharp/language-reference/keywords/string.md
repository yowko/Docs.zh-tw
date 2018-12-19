---
title: string - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: f6c76f8effc5aef82803014b9a7257c2ad6865b8
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286477"
---
# <a name="string-c-reference"></a>string (C# 參考)

`string` 類型代表零或多個 Unicode 字元序列。 `string` 是 <xref:System.String> 在 .NET 中的別名。

雖然 `string` 是參考型別，但是定義等號比較運算子 (`==` 和 `!=`) 來比較 `string` 物件的值，而不是參考。 這樣會以更直覺的方式來測試字串是否相等。 例如: 

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

這會依序顯示 "True" 和 "False"，因為字串的內容相等，但 `a` 和 `b` 未參照相同的字串執行個體。

+ 運算子會串連字串：

```csharp
string a = "good " + "morning";
```

這會建立包含 "good morning" 的字串物件。

字串是「不可變的」；在建立物件之後，就無法變更字串物件的內容，雖然語法讓它看起來就像您可以這麼做一樣。 例如，當您撰寫此程式碼時，編譯器實際上會建立新的字串物件，以保存新序列的字元，並且會將新物件指派給 b。 字串 "h" 接著會適合進行記憶體回收。

```csharp
string b = "h";
b += "ello";
```

[] 運算子可以用於唯讀存取 `string` 的個別字元：

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

類似地，[] 運算子也可以用來逐一查看 `string` 中的每個字元：

```csharp
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

字串常值的類型是 `string`，可以撰寫為兩種形式：quoted 和 @-quoted。 以引號括住的字串常值是以雙引號 (") 括住：

```csharp
"good morning"  // a string literal
```

字串常值可以包含任何字元常值。 包含逸出序列。 下列範例使用逸出序列 `\\` 表示反斜線、`\u0066` 表示字母 f，而 `\n` 表示新行字元。

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> 逸出代碼 `\udddd` (其中 `dddd` 是四位數字) 代表 Unicode 字元 U+`dddd`。 也會辨識八位數 Unicode 逸出代碼︰`\Udddddddd`。

逐字字串常值的開頭為 `@`，也會用雙引號括住。 例如: 

```csharp
@"good morning"  // a string literal
```

逐字字串的優點是「不」會處理逸出序列，例如，這可讓您輕鬆地撰寫完整檔案名稱︰

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

若要在 @-quoted 字串中包含雙引號，請使用兩個雙引號︰

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

若要了解 `@` 特殊字元的其他使用方法，請參閱 [@ -- 逐字識別項](../tokens/verbatim.md)。

如需 C# 中字串的詳細資訊，請參閱[字串](../../programming-guide/strings/index.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [使用字串的最佳做法](../../../standard/base-types/best-practices-strings.md)
- [C# 關鍵字](index.md)
- [參考型別](reference-types.md)
- [實值型別](value-types.md)
- [基本字串作業](../../../standard/base-types/basic-string-operations.md)
- [建立新字串](../../../standard/base-types/creating-new.md)
- [格式化數值結果表](formatting-numeric-results-table.md)
