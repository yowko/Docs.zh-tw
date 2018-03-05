---
title: "字串插值 (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="4192f-102">字串插值 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4192f-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="4192f-103">可用來建構字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-103">Used to construct strings.</span></span>  <span data-ttu-id="4192f-104">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="4192f-105">字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="4192f-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="4192f-106">C# 6 及更新版本有提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="4192f-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="4192f-107">字串插值的引數比[複合格式字串](../../../standard/base-types/composite-formatting.md#composite-format-string)更容易了解。</span><span class="sxs-lookup"><span data-stu-id="4192f-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="4192f-108">例如，字串插值</span><span class="sxs-lookup"><span data-stu-id="4192f-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="4192f-109">包含兩個插入運算式 '{name}' 和 '{hours:hh}'。</span><span class="sxs-lookup"><span data-stu-id="4192f-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="4192f-110">對等的複合格式字串為：</span><span class="sxs-lookup"><span data-stu-id="4192f-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="4192f-111">字串插值的結構為：</span><span class="sxs-lookup"><span data-stu-id="4192f-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="4192f-112">其中：</span><span class="sxs-lookup"><span data-stu-id="4192f-112">where:</span></span> 

- <span data-ttu-id="4192f-113">*field-width* 是帶正負號的整數，表示欄位中的字元數。</span><span class="sxs-lookup"><span data-stu-id="4192f-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="4192f-114">如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="4192f-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="4192f-115">*format-string* 是一個格式字串，適用於將格式化的物件類型。</span><span class="sxs-lookup"><span data-stu-id="4192f-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="4192f-116">例如，若為 <xref:System.DateTime> 值，它可能是標準日期和時間格式字串，像是 "D" 或 "d"。</span><span class="sxs-lookup"><span data-stu-id="4192f-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4192f-117">字串開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="4192f-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="4192f-118">這樣做會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="4192f-118">Doing so causes a compile time error.</span></span>

 <span data-ttu-id="4192f-119">您可以在使用字串常值的任何位置使用字串插值。</span><span class="sxs-lookup"><span data-stu-id="4192f-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="4192f-120">每次執行含有字串插值的程式碼時，都會評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="4192f-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="4192f-121">這可讓您分開定義和評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="4192f-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="4192f-122">若要在字串插值中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="4192f-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="4192f-123">如需詳細資訊，請參閱＜隱含轉換＞一節。</span><span class="sxs-lookup"><span data-stu-id="4192f-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="4192f-124">當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。</span><span class="sxs-lookup"><span data-stu-id="4192f-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="4192f-125">下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="4192f-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="4192f-126">逐字內插字串使用 `$` 字元，後面接著 `@` 字元。</span><span class="sxs-lookup"><span data-stu-id="4192f-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="4192f-127">如需逐字字串的詳細資訊，請參閱[字串](string.md)主題。</span><span class="sxs-lookup"><span data-stu-id="4192f-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="4192f-128">下列程式碼是先前使用逐字內插字串之程式碼片段的已修改版本：</span><span class="sxs-lookup"><span data-stu-id="4192f-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="4192f-129">由於逐字字串未遵循 `\` 逸出序列，因此需要格式變更。</span><span class="sxs-lookup"><span data-stu-id="4192f-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4192f-130">`$` 語彙基元必須出現在逐字內插字串中的 `@` 語彙基元之前。</span><span class="sxs-lookup"><span data-stu-id="4192f-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="4192f-131">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="4192f-131">Implicit Conversions</span></span>  

<span data-ttu-id="4192f-132">有三個來自字串插值的隱含型別轉換：</span><span class="sxs-lookup"><span data-stu-id="4192f-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="4192f-133">將字串插值轉換成 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="4192f-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="4192f-134">下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="4192f-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="4192f-135">例如: </span><span class="sxs-lookup"><span data-stu-id="4192f-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="4192f-136">這是字串解譯的最終結果。</span><span class="sxs-lookup"><span data-stu-id="4192f-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="4192f-137">所有出現的雙大括弧 ("{{" 和 "}}") 都會轉換成單一大括弧。</span><span class="sxs-lookup"><span data-stu-id="4192f-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="4192f-138">將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="4192f-139">若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。</span><span class="sxs-lookup"><span data-stu-id="4192f-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="4192f-140">在您明確或隱含呼叫 <xref:System.Object.ToString> 方法以格式化字串之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="4192f-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="4192f-141">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="4192f-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="4192f-142">下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。</span><span class="sxs-lookup"><span data-stu-id="4192f-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="4192f-143">它也會將 <xref:System.IFormattable> 變數傳遞給 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4192f-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="4192f-144">請注意，只能使用反映來檢查字串插值。</span><span class="sxs-lookup"><span data-stu-id="4192f-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="4192f-145">如果將它傳遞至字串格式化方法 (例如 <xref:System.Console.WriteLine(System.String)>)，則會解析其格式項目並傳回結果字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="4192f-146">將字串插值轉換成 <xref:System.FormattableString> 變數，以代表複合格式字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="4192f-147">檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="4192f-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="4192f-148"><xref:System.FormattableString> 也包含 <xref:System.FormattableString.ToString> 多載，可讓您產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 和 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串。</span><span class="sxs-lookup"><span data-stu-id="4192f-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="4192f-149">在您格式化之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="4192f-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="4192f-150">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="4192f-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="4192f-151">語言規格</span><span class="sxs-lookup"><span data-stu-id="4192f-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4192f-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="4192f-152">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="4192f-153">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4192f-153">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4192f-154">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4192f-154">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
