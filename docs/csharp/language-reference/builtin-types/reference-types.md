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
ms.openlocfilehash: a5a32fa0a98cda37d7f599b20ef2b507cadd730c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69604208"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="fcc93-103">內建參考型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fcc93-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="fcc93-104">C# 有數種內建參考型別。</span><span class="sxs-lookup"><span data-stu-id="fcc93-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="fcc93-105">它們具有關鍵字或運算子，是 .NET 程式庫中類型的同義字。</span><span class="sxs-lookup"><span data-stu-id="fcc93-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="fcc93-106">物件型別</span><span class="sxs-lookup"><span data-stu-id="fcc93-106">The object type</span></span>

<span data-ttu-id="fcc93-107">`object` 類型是 <xref:System.Object?displayProperty=nameWithType> 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="fcc93-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="fcc93-108">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fcc93-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fcc93-109">您可以將任何型別的值指派給 `object` 型別的變數。</span><span class="sxs-lookup"><span data-stu-id="fcc93-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="fcc93-110">任何 `object` 變數都可以使用常值 `null` 指派給其預設值。</span><span class="sxs-lookup"><span data-stu-id="fcc93-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="fcc93-111">當實值型別的變數轉換成物件時，即稱之為 *Boxed*。</span><span class="sxs-lookup"><span data-stu-id="fcc93-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="fcc93-112">當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。</span><span class="sxs-lookup"><span data-stu-id="fcc93-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="fcc93-113">如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc93-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="fcc93-114">字串型別</span><span class="sxs-lookup"><span data-stu-id="fcc93-114">The string type</span></span>

<span data-ttu-id="fcc93-115">`string` 類型代表零或多個 Unicode 字元序列。</span><span class="sxs-lookup"><span data-stu-id="fcc93-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="fcc93-116">`string` 是 <xref:System.String?displayProperty=nameWithType> 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="fcc93-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="fcc93-117">雖然 `string` 是參考型別，但是會定義[等號比較運算子 `==` 和 `!=`](../operators/equality-operators.md#string-equality) 來比較 `string` 物件的值，而不是參考。</span><span class="sxs-lookup"><span data-stu-id="fcc93-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="fcc93-118">這樣會以更直覺的方式來測試字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="fcc93-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="fcc93-119">例如:</span><span class="sxs-lookup"><span data-stu-id="fcc93-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="fcc93-120">這會依序顯示 "True" 和 "False"，因為字串的內容相等，但 `a` 和 `b` 未參照相同的字串執行個體。</span><span class="sxs-lookup"><span data-stu-id="fcc93-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="fcc93-121">[+ 運算子](../operators/addition-operator.md#string-concatenation)會串連字串：</span><span class="sxs-lookup"><span data-stu-id="fcc93-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="fcc93-122">這會建立包含 "good morning" 的字串物件。</span><span class="sxs-lookup"><span data-stu-id="fcc93-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="fcc93-123">字串是「不可變的」  ；在建立物件之後，就無法變更字串物件的內容，雖然語法讓它看起來就像您可以這麼做一樣。</span><span class="sxs-lookup"><span data-stu-id="fcc93-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="fcc93-124">例如，當您撰寫此程式碼時，編譯器實際上會建立新的字串物件，以保存新序列的字元，並且會將新物件指派給 `b`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="fcc93-125">已配置給 `b` 的記憶體 (當其包含字串 "h" 時) 即適用於記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="fcc93-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="fcc93-126">`[]` [運算子](../operators/member-access-operators.md#indexer-operator-)可以用於唯讀存取 `string` 的個別字元。</span><span class="sxs-lookup"><span data-stu-id="fcc93-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="fcc93-127">有效的值從 `0` 開始，且必須小於 `string` 的長度：</span><span class="sxs-lookup"><span data-stu-id="fcc93-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="fcc93-128">類似地，`[]` 運算子也可以用來逐一查看 `string` 中的每個字元：</span><span class="sxs-lookup"><span data-stu-id="fcc93-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="fcc93-129">字串常值的型別是 `string`，可以撰寫為兩種形式：quoted 和 `@`-quoted。</span><span class="sxs-lookup"><span data-stu-id="fcc93-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="fcc93-130">以引號括住的字串常值是以雙引號 (") 括住：</span><span class="sxs-lookup"><span data-stu-id="fcc93-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="fcc93-131">字串常值可以包含任何字元常值。</span><span class="sxs-lookup"><span data-stu-id="fcc93-131">String literals can contain any character literal.</span></span> <span data-ttu-id="fcc93-132">包含逸出序列。</span><span class="sxs-lookup"><span data-stu-id="fcc93-132">Escape sequences are included.</span></span> <span data-ttu-id="fcc93-133">下列範例使用逸出序列 `\\` 表示反斜線、`\u0066` 表示字母 f，而 `\n` 表示新行字元。</span><span class="sxs-lookup"><span data-stu-id="fcc93-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="fcc93-134">逸出代碼 `\udddd` (其中 `dddd` 是四位數字) 代表 Unicode 字元 U+`dddd`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="fcc93-135">也會辨識八位數 Unicode 逸出代碼︰`\Udddddddd`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="fcc93-136">[逐字字串常值](../tokens/verbatim.md)的開頭為 `@`，也會用雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="fcc93-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="fcc93-137">例如：</span><span class="sxs-lookup"><span data-stu-id="fcc93-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="fcc93-138">逐字字串的優點是「不會」  處理逸出序列，例如，這可讓您輕鬆地撰寫完整 Windows 檔案名稱︰</span><span class="sxs-lookup"><span data-stu-id="fcc93-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="fcc93-139">若要在 @-quoted 字串中包含雙引號，請使用兩個雙引號︰</span><span class="sxs-lookup"><span data-stu-id="fcc93-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="fcc93-140">委派型別</span><span class="sxs-lookup"><span data-stu-id="fcc93-140">The delegate type</span></span>

<span data-ttu-id="fcc93-141">委派類型的宣告類似方法簽章。</span><span class="sxs-lookup"><span data-stu-id="fcc93-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="fcc93-142">它具有傳回值以及任意類型之任何數目的參數：</span><span class="sxs-lookup"><span data-stu-id="fcc93-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="fcc93-143">在 .NET 中，`System.Action` 和 `System.Func` 型別提供許多常見委派的泛型定義。</span><span class="sxs-lookup"><span data-stu-id="fcc93-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="fcc93-144">您多半不需要定義新的自訂委派型別。</span><span class="sxs-lookup"><span data-stu-id="fcc93-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="fcc93-145">反之，您可以建立所提供之泛型型別的具現化。</span><span class="sxs-lookup"><span data-stu-id="fcc93-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="fcc93-146">`delegate` 是可用來封裝具名或匿名方法的參考型別。</span><span class="sxs-lookup"><span data-stu-id="fcc93-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="fcc93-147">委派類似 C++ 中的函式指標，但委派是型別安全而且安全的。</span><span class="sxs-lookup"><span data-stu-id="fcc93-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="fcc93-148">如需委派的應用程式，請參閱[委派](../../programming-guide/delegates/index.md)和[泛型委派](../../programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc93-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="fcc93-149">委派是[事件](../../programming-guide/events/index.md)的基礎。</span><span class="sxs-lookup"><span data-stu-id="fcc93-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="fcc93-150">委派的具現化方式是將它與具名或匿名方法建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fcc93-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="fcc93-151">委派必須使用具有相容傳回型別和輸入參數的方法或 Lambda 運算式進行具現化。</span><span class="sxs-lookup"><span data-stu-id="fcc93-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="fcc93-152">如需方法簽章中所允許變異程度的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) (委派中的變異數)。</span><span class="sxs-lookup"><span data-stu-id="fcc93-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="fcc93-153">若與匿名方法搭配使用，則會一起宣告要與它建立關聯的委派和程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcc93-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="fcc93-154">動態型別</span><span class="sxs-lookup"><span data-stu-id="fcc93-154">The dynamic type</span></span>

<span data-ttu-id="fcc93-155">`dynamic` 型別指出使用變數和對其成員的參考，會略過編譯時間型別檢查。</span><span class="sxs-lookup"><span data-stu-id="fcc93-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="fcc93-156">相反地，這些作業會在執行階段解決。</span><span class="sxs-lookup"><span data-stu-id="fcc93-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="fcc93-157">`dynamic` 類型會簡化 Office Automation API 這類 COM API 的存取、IronPython 程式庫這類動態 API 的存取，以及 HTML 文件物件模型 (DOM) 的存取。</span><span class="sxs-lookup"><span data-stu-id="fcc93-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="fcc93-158">在大多數情況下，`dynamic` 類型的行為與 `object` 類型類似。</span><span class="sxs-lookup"><span data-stu-id="fcc93-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="fcc93-159">特別是，任何非 Null 運算式都可轉換成 `dynamic` 型別。</span><span class="sxs-lookup"><span data-stu-id="fcc93-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="fcc93-160">`dynamic` 型別與 `object` 的不同之處在於，包含型別 `dynamic` 運算式的操作，不會由編譯器解析或進行型別檢查。</span><span class="sxs-lookup"><span data-stu-id="fcc93-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="fcc93-161">編譯器會將作業資訊封裝在一起，而且稍後在執行階段會使用這項資訊來評估作業。</span><span class="sxs-lookup"><span data-stu-id="fcc93-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="fcc93-162">在此程序期間，會將 `dynamic` 類型的變數編譯為 `object` 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="fcc93-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="fcc93-163">因此，`dynamic` 類型只存在於編譯時期，而非執行階段。</span><span class="sxs-lookup"><span data-stu-id="fcc93-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="fcc93-164">下列範例會對照 `dynamic` 類型的變數與 `object` 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="fcc93-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="fcc93-165">若要在編譯時期驗證每個變數的類型，請將滑鼠指標放在 `WriteLine` 陳述式中的 `dyn` 或 `obj` 上方。</span><span class="sxs-lookup"><span data-stu-id="fcc93-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="fcc93-166">將下列程式碼複製到可使用 IntelliSense 的編輯器。</span><span class="sxs-lookup"><span data-stu-id="fcc93-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="fcc93-167">IntelliSense 會顯示「動態」  來表示 `dyn`，並顯示「物件」  來表示 `obj`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="fcc93-168"><xref:System.Console.WriteLine%2A> 陳述式會顯示執行階段類型 `dyn` 和 `obj`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="fcc93-169">此時，兩者都有相同的類型：整數。</span><span class="sxs-lookup"><span data-stu-id="fcc93-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="fcc93-170">會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fcc93-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="fcc93-171">若要查看 `dyn` 與 `obj` 在編譯時期的差異，請在上述範例的宣告與 `WriteLine` 陳述式之間新增下列兩行。</span><span class="sxs-lookup"><span data-stu-id="fcc93-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="fcc93-172">嘗試新增運算式 `obj + 3` 中的整數和物件時報告編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="fcc93-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="fcc93-173">不過，不會回報 `dyn + 3` 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fcc93-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="fcc93-174">在編譯時期不會檢查包含 `dyn` 的運算式，因為 `dyn` 的類型是 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="fcc93-175">下列範例會在數個宣告中使用 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="fcc93-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="fcc93-176">`Main` 方法也會對照編譯時期類型檢查與執行階段類型檢查。</span><span class="sxs-lookup"><span data-stu-id="fcc93-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="fcc93-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc93-177">See also</span></span>

- [<span data-ttu-id="fcc93-178">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fcc93-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fcc93-179">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="fcc93-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="fcc93-180">事件</span><span class="sxs-lookup"><span data-stu-id="fcc93-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="fcc93-181">使用動態型別</span><span class="sxs-lookup"><span data-stu-id="fcc93-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="fcc93-182">使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="fcc93-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="fcc93-183">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="fcc93-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="fcc93-184">建立新字串</span><span class="sxs-lookup"><span data-stu-id="fcc93-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="fcc93-185">型別測試和轉換運算子</span><span class="sxs-lookup"><span data-stu-id="fcc93-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="fcc93-186">如何：使用模式比對、as 和 is 運算子，安全地進行轉換</span><span class="sxs-lookup"><span data-stu-id="fcc93-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="fcc93-187">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="fcc93-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
