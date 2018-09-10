---
title: string (C# 參考)
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
ms.openlocfilehash: 8b70f1c1dcb39dcdde6ba24a1bdcdfc3084cfc97
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513096"
---
# <a name="string-c-reference"></a><span data-ttu-id="366ff-102">string (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="366ff-102">string (C# Reference)</span></span>
<span data-ttu-id="366ff-103">`string` 類型代表零或多個 Unicode 字元序列。</span><span class="sxs-lookup"><span data-stu-id="366ff-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="366ff-104">`string` 是 <xref:System.String> 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="366ff-104">`string` is an alias for <xref:System.String> in .NET.</span></span>  
  
 <span data-ttu-id="366ff-105">雖然 `string` 是參考型別，但是定義等號比較運算子 (`==` 和 `!=`) 來比較 `string` 物件的值，而不是參考。</span><span class="sxs-lookup"><span data-stu-id="366ff-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="366ff-106">這樣會以更直覺的方式來測試字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="366ff-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="366ff-107">例如: </span><span class="sxs-lookup"><span data-stu-id="366ff-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="366ff-108">這會依序顯示 "True" 和 "False"，因為字串的內容相等，但 `a` 和 `b` 未參照相同的字串執行個體。</span><span class="sxs-lookup"><span data-stu-id="366ff-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="366ff-109">+ 運算子會串連字串：</span><span class="sxs-lookup"><span data-stu-id="366ff-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="366ff-110">這會建立包含 "good morning" 的字串物件。</span><span class="sxs-lookup"><span data-stu-id="366ff-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="366ff-111">字串是「不可變的」；在建立物件之後，就無法變更字串物件的內容，雖然語法讓它看起來就像您可以這麼做一樣。</span><span class="sxs-lookup"><span data-stu-id="366ff-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="366ff-112">例如，當您撰寫此程式碼時，編譯器實際上會建立新的字串物件，以保存新序列的字元，並且會將新物件指派給 b。</span><span class="sxs-lookup"><span data-stu-id="366ff-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="366ff-113">字串 "h" 接著會適合進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="366ff-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="366ff-114">[] 運算子可以用於唯讀存取 `string` 的個別字元：</span><span class="sxs-lookup"><span data-stu-id="366ff-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="366ff-115">字串常值的類型是 `string`，可以撰寫為兩種形式：quoted 和 @-quoted。</span><span class="sxs-lookup"><span data-stu-id="366ff-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="366ff-116">以引號括住的字串常值是以雙引號 (") 括住：</span><span class="sxs-lookup"><span data-stu-id="366ff-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="366ff-117">字串常值可以包含任何字元常值。</span><span class="sxs-lookup"><span data-stu-id="366ff-117">String literals can contain any character literal.</span></span> <span data-ttu-id="366ff-118">包含逸出序列。</span><span class="sxs-lookup"><span data-stu-id="366ff-118">Escape sequences are included.</span></span> <span data-ttu-id="366ff-119">下列範例使用逸出序列 `\\` 表示反斜線、`\u0066` 表示字母 f，而 `\n` 表示新行字元。</span><span class="sxs-lookup"><span data-stu-id="366ff-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```csharp  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="366ff-120">逸出代碼 `\udddd` (其中 `dddd` 是四位數字) 代表 Unicode 字元 U+`dddd`。</span><span class="sxs-lookup"><span data-stu-id="366ff-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="366ff-121">也會辨識八位數 Unicode 逸出代碼︰`\Udddddddd`。</span><span class="sxs-lookup"><span data-stu-id="366ff-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="366ff-122">逐字字串常值的開頭為 `@`，也會用雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="366ff-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="366ff-123">例如: </span><span class="sxs-lookup"><span data-stu-id="366ff-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="366ff-124">逐字字串的優點是「不」會處理逸出序列，例如，這可讓您輕鬆地撰寫完整檔案名稱︰</span><span class="sxs-lookup"><span data-stu-id="366ff-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="366ff-125">若要在 @-quoted 字串中包含雙引號，請使用兩個雙引號︰</span><span class="sxs-lookup"><span data-stu-id="366ff-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="366ff-126">若要了解 `@` 特殊字元的其他使用方法，請參閱 [@ -- 逐字識別項](../tokens/verbatim.md)。</span><span class="sxs-lookup"><span data-stu-id="366ff-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>  
  
 <span data-ttu-id="366ff-127">如需 C# 中字串的詳細資訊，請參閱[字串](../../../csharp/programming-guide/strings/index.md)。</span><span class="sxs-lookup"><span data-stu-id="366ff-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="366ff-128">範例</span><span class="sxs-lookup"><span data-stu-id="366ff-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="366ff-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="366ff-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="366ff-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="366ff-130">See Also</span></span>

- [<span data-ttu-id="366ff-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="366ff-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="366ff-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="366ff-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="366ff-133">使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="366ff-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
- [<span data-ttu-id="366ff-134">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="366ff-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="366ff-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="366ff-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="366ff-136">參考型別</span><span class="sxs-lookup"><span data-stu-id="366ff-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="366ff-137">實值型別</span><span class="sxs-lookup"><span data-stu-id="366ff-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="366ff-138">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="366ff-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
- [<span data-ttu-id="366ff-139">建立新字串</span><span class="sxs-lookup"><span data-stu-id="366ff-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
- [<span data-ttu-id="366ff-140">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="366ff-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
