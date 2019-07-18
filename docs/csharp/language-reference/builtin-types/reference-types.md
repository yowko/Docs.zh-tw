---
title: 內建參考型別 - C# 參考
description: 了解具有 C# 關鍵字的參考型別，您可以用來宣告它們。
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67872166"
---
# <a name="built-in-reference-types-c-reference"></a>內建參考型別 (C# 參考)

C# 有數種內建參考型別。 它們具有關鍵字或運算子，是 .NET 程式庫中類型的同義字。 

## <a name="the-object-type"></a>物件型別

`object` 類型是 <xref:System.Object?displayProperty=nameWithType> 在 .NET 中的別名。 在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object?displayProperty=nameWithType>。 您可以將任何型別的值指派給 `object` 型別的變數。 任何 `object` 變數都可以使用常值 `null` 指派給其預設值。 當實值型別的變數轉換成物件時，即稱之為 *Boxed*。 當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../programming-guide/types/boxing-and-unboxing.md)。 

## <a name="the-string-type"></a>字串型別

`string` 類型代表零或多個 Unicode 字元序列。 `string` 是 <xref:System.String?displayProperty=nameWithType> 在 .NET 中的別名。

雖然 `string` 是參考型別，但是會定義[等號比較運算子 `==` 和 `!=`](../operators/equality-operators.md#string-equality) 來比較 `string` 物件的值，而不是參考。 這樣會以更直覺的方式來測試字串是否相等。 例如:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

這會依序顯示 "True" 和 "False"，因為字串的內容相等，但 `a` 和 `b` 未參照相同的字串執行個體。

[+ 運算子](../operators/addition-operator.md#string-concatenation)會串連字串：

```csharp
string a = "good " + "morning";
```

這會建立包含 "good morning" 的字串物件。

字串是「不可變的」  ；在建立物件之後，就無法變更字串物件的內容，雖然語法讓它看起來就像您可以這麼做一樣。 例如，當您撰寫此程式碼時，編譯器實際上會建立新的字串物件，以保存新序列的字元，並且會將新物件指派給 `b`。 已配置給 `b` 的記憶體 (當其包含字串 "h" 時) 即適用於記憶體回收。

```csharp
string b = "h";
b += "ello";
```

`[]` [運算子](../operators/member-access-operators.md#indexer-operator-)可以用於唯讀存取 `string` 的個別字元。 有效的值從 `0` 開始，且必須小於 `string` 的長度：

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

類似地，`[]` 運算子也可以用來逐一查看 `string` 中的每個字元：

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

字串常值的型別是 `string`，可以撰寫為兩種形式：quoted 和 `@`-quoted。 以引號括住的字串常值是以雙引號 (") 括住：

```csharp
"good morning"  // a string literal
```

字串常值可以包含任何字元常值。 包含逸出序列。 下列範例使用逸出序列 `\\` 表示反斜線、`\u0066` 表示字母 f，而 `\n` 表示新行字元。

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> 逸出代碼 `\udddd` (其中 `dddd` 是四位數字) 代表 Unicode 字元 U+`dddd`。 也會辨識八位數 Unicode 逸出代碼︰`\Udddddddd`。

[逐字字串常值](../tokens/verbatim.md)的開頭為 `@`，也會用雙引號括住。 例如：

```csharp
@"good morning"  // a string literal
```

逐字字串的優點是「不會」  處理逸出序列，例如，這可讓您輕鬆地撰寫完整 Windows 檔案名稱︰

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

若要在 @-quoted 字串中包含雙引號，請使用兩個雙引號︰

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>委派型別

委派類型的宣告類似方法簽章。 它具有傳回值以及任意類型之任何數目的參數：

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

在 .NET 中，`System.Action` 和 `System.Func` 型別提供許多常見委派的泛型定義。 您多半不需要定義新的自訂委派型別。 反之，您可以建立所提供之泛型型別的具現化。

`delegate` 是可用來封裝具名或匿名方法的參考型別。 委派類似 C++ 中的函式指標，但委派是型別安全而且安全的。 如需委派的應用程式，請參閱[委派](../../programming-guide/delegates/index.md)和[泛型委派](../../programming-guide/generics/generic-delegates.md)。 委派是[事件](../../programming-guide/events/index.md)的基礎。 委派的具現化方式是將它與具名或匿名方法建立關聯。

委派必須使用具有相容傳回型別和輸入參數的方法或 Lambda 運算式進行具現化。 如需方法簽章中所允許變異程度的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) (委派中的變異數)。 若與匿名方法搭配使用，則會一起宣告要與它建立關聯的委派和程式碼。 

## <a name="the-dynamic-type"></a>動態型別

`dynamic` 型別指出使用變數和對其成員的參考，會略過編譯時間型別檢查。 相反地，這些作業會在執行階段解決。 `dynamic` 類型會簡化 Office Automation API 這類 COM API 的存取、IronPython 程式庫這類動態 API 的存取，以及 HTML 文件物件模型 (DOM) 的存取。

在大多數情況下，`dynamic` 類型的行為與 `object` 類型類似。 特別是，任何非 Null 運算式都可轉換成 `dynamic` 型別。 `dynamic` 型別與 `object` 的不同之處在於，包含型別 `dynamic` 運算式的操作，不會由編譯器解析或進行型別檢查。 編譯器會將作業資訊封裝在一起，而且稍後在執行階段會使用這項資訊來評估作業。 在此程序期間，會將 `dynamic` 類型的變數編譯為 `object` 類型的變數。 因此，`dynamic` 類型只存在於編譯時期，而非執行階段。

下列範例會對照 `dynamic` 類型的變數與 `object` 類型的變數。 若要在編譯時期驗證每個變數的類型，請將滑鼠指標放在 `WriteLine` 陳述式中的 `dyn` 或 `obj` 上方。 將下列程式碼複製到可使用 IntelliSense 的編輯器。 IntelliSense 會顯示「動態」  來表示 `dyn`，並顯示「物件」  來表示 `obj`。

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> 陳述式會顯示執行階段類型 `dyn` 和 `obj`。 此時，兩者都有相同的類型：整數。 會產生下列輸出：

```console
System.Int32
System.Int32
```

若要查看 `dyn` 與 `obj` 在編譯時期的差異，請在上述範例的宣告與 `WriteLine` 陳述式之間新增下列兩行。

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 嘗試新增運算式 `obj + 3` 中的整數和物件時報告編譯器錯誤。 不過，不會回報 `dyn + 3` 的錯誤。 在編譯時期不會檢查包含 `dyn` 的運算式，因為 `dyn` 的類型是 `dynamic`。

下列範例會在數個宣告中使用 `dynamic`。 `Main` 方法也會對照編譯時期類型檢查與執行階段類型檢查。

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 關鍵字](../keywords/index.md)
- [事件](../../../csharp/programming-guide/events/index.md)
- [使用動態型別](../../programming-guide/types/using-type-dynamic.md)
- [使用字串的最佳做法](../../../standard/base-types/best-practices-strings.md)
- [基本字串作業](../../../standard/base-types/basic-string-operations.md)
- [建立新字串](../../../standard/base-types/creating-new.md)
- [類型測試和轉換運算子](../operators/type-testing-and-conversion-operators.md)
- [如何：使用模式比對、as 和 is 運算子，安全地進行轉換](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [逐步解說：建立和使用動態物件](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
