---
title: 字串插值 (Visual Basic)
ms.date: 10/31/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9501c052f387a522226e957193a8866083aa4233
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="2564e-102">字串插值 （Visual Basic 參考）</span><span class="sxs-lookup"><span data-stu-id="2564e-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="2564e-103">可用來建構字串。</span><span class="sxs-lookup"><span data-stu-id="2564e-103">Used to construct strings.</span></span>  <span data-ttu-id="2564e-104">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="2564e-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="2564e-105">字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="2564e-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="2564e-106">Visual Basic 14 和更新版本中使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="2564e-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="2564e-107">字串插值的引數比[複合格式字串](../../../../standard/base-types/composite-formatting.md#composite-format-string)更容易了解。</span><span class="sxs-lookup"><span data-stu-id="2564e-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="2564e-108">例如，字串插值</span><span class="sxs-lookup"><span data-stu-id="2564e-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="2564e-109">包含兩個插入運算式 '{name}' 和 '{hours:hh}'。</span><span class="sxs-lookup"><span data-stu-id="2564e-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="2564e-110">對等的複合格式字串為：</span><span class="sxs-lookup"><span data-stu-id="2564e-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="2564e-111">字串插值的結構為：</span><span class="sxs-lookup"><span data-stu-id="2564e-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="2564e-112">其中：</span><span class="sxs-lookup"><span data-stu-id="2564e-112">where:</span></span> 

- <span data-ttu-id="2564e-113">*field-width* 是帶正負號的整數，表示欄位中的字元數。</span><span class="sxs-lookup"><span data-stu-id="2564e-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="2564e-114">如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="2564e-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="2564e-115">*format-string* 是一個格式字串，適用於將格式化的物件類型。</span><span class="sxs-lookup"><span data-stu-id="2564e-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="2564e-116">例如，對於<xref:System.DateTime>值，它可能是[標準日期和時間格式字串](~/docs/standard/base-types/standard-date-and-time-format-strings.md)例如"D"或"d"。</span><span class="sxs-lookup"><span data-stu-id="2564e-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2564e-117">字串開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="2564e-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="2564e-118">這樣做會讓編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="2564e-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="2564e-119">您可以在使用字串常值的任何位置使用字串插值。</span><span class="sxs-lookup"><span data-stu-id="2564e-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="2564e-120">每次執行含有字串插值的程式碼時，都會評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="2564e-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="2564e-121">這可讓您分開定義和評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="2564e-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="2564e-122">若要在字串插值中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="2564e-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="2564e-123">如需詳細資訊，請參閱＜隱含轉換＞一節。</span><span class="sxs-lookup"><span data-stu-id="2564e-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="2564e-124">當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。</span><span class="sxs-lookup"><span data-stu-id="2564e-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="2564e-125">下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="2564e-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="2564e-126">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="2564e-126">Implicit Conversions</span></span>  

<span data-ttu-id="2564e-127">有三個來自字串插值的隱含型別轉換：</span><span class="sxs-lookup"><span data-stu-id="2564e-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="2564e-128">將字串插值轉換成 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="2564e-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="2564e-129">下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="2564e-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="2564e-130">例如: </span><span class="sxs-lookup"><span data-stu-id="2564e-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="2564e-131">這是字串解譯的最終結果。</span><span class="sxs-lookup"><span data-stu-id="2564e-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="2564e-132">所有出現的雙大括弧 ("{{" 和 "}}") 都會轉換成單一大括弧。</span><span class="sxs-lookup"><span data-stu-id="2564e-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="2564e-133">將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="2564e-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="2564e-134">若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。</span><span class="sxs-lookup"><span data-stu-id="2564e-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="2564e-135">在您明確或隱含呼叫 <xref:System.Object.ToString> 方法以格式化字串之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="2564e-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="2564e-136">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="2564e-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="2564e-137">下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。</span><span class="sxs-lookup"><span data-stu-id="2564e-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="2564e-138">它也會將 <xref:System.IFormattable> 變數傳遞給 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2564e-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="2564e-139">請注意，只能使用反映來檢查字串插值。</span><span class="sxs-lookup"><span data-stu-id="2564e-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="2564e-140">如果將它傳遞至字串格式化方法 (例如 <xref:System.Console.WriteLine(System.String)>)，則會解析其格式項目並傳回結果字串。</span><span class="sxs-lookup"><span data-stu-id="2564e-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="2564e-141">轉換至字串插值的<xref:System.FormattableString>代表複合格式字串的變數。</span><span class="sxs-lookup"><span data-stu-id="2564e-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="2564e-142">檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="2564e-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="2564e-143">A<xref:System.FormattableString>還包括：</span><span class="sxs-lookup"><span data-stu-id="2564e-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="2564e-144">A<xref:System.FormattableString.ToString>產生的結果字串的多載<xref:System.Globalization.CultureInfo.CurrentCulture>。</span><span class="sxs-lookup"><span data-stu-id="2564e-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="2564e-145">A<xref:System.FormattableString.Invariant%2A>方法所產生的字串<xref:System.Globalization.CultureInfo.InvariantCulture>。</span><span class="sxs-lookup"><span data-stu-id="2564e-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="2564e-146">A<xref:System.FormattableString.ToString(System.IFormatProvider)>產生的結果字串會指定文化特性的方法。</span><span class="sxs-lookup"><span data-stu-id="2564e-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="2564e-147">所有出現的雙大括弧 ("{{"和"}}") 保持為雙大括弧，直到您格式化為止。</span><span class="sxs-lookup"><span data-stu-id="2564e-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="2564e-148">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="2564e-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="2564e-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2564e-149">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="2564e-150">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="2564e-150">Visual Basic Language Reference</span></span>](index.md)  
 