---
title: "字串插值 (C#) | Microsoft Docs"
ms.date: 2017-02-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: be7974018ce3195dc7344192d647fe64fb2ebcc4
ms.openlocfilehash: ee9d0f9803c6de056644587578792568ab25b4da
ms.contentlocale: zh-tw
ms.lasthandoff: 05/14/2017

---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="e0464-102">字串插值 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e0464-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="e0464-103">可用來建構字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-103">Used to construct strings.</span></span>  <span data-ttu-id="e0464-104">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="e0464-105">字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="e0464-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span>  

<span data-ttu-id="e0464-106">字串插值的引數比[複合格式字串](../../../standard/base-types/composite-formatting.md#composite-format-string)更容易了解。</span><span class="sxs-lookup"><span data-stu-id="e0464-106">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="e0464-107">例如，字串插值</span><span class="sxs-lookup"><span data-stu-id="e0464-107">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}"); 
```  
<span data-ttu-id="e0464-108">包含兩個插入運算式 '{name}' 和 '{hours:hh}'。</span><span class="sxs-lookup"><span data-stu-id="e0464-108">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="e0464-109">對等的複合格式字串為：</span><span class="sxs-lookup"><span data-stu-id="e0464-109">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);  
```  

<span data-ttu-id="e0464-110">字串插值的結構為：</span><span class="sxs-lookup"><span data-stu-id="e0464-110">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [<:format-string>] } <text> ..."  
```  

<span data-ttu-id="e0464-111">其中：</span><span class="sxs-lookup"><span data-stu-id="e0464-111">where:</span></span> 

- <span data-ttu-id="e0464-112">*field-width* 是帶正負號的整數，表示欄位中的字元數。</span><span class="sxs-lookup"><span data-stu-id="e0464-112">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="e0464-113">如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="e0464-113">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="e0464-114">*format-string* 是一個格式字串，適用於將格式化的物件類型。</span><span class="sxs-lookup"><span data-stu-id="e0464-114">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="e0464-115">例如，若為 @System.DateTime 值，它可能是標準日期和時間格式字串，像是 "D" 或 "d"。</span><span class="sxs-lookup"><span data-stu-id="e0464-115">For example, for a @System.DateTime value, it could be a standard date and time format string such as "D" or "d".</span></span>

 <span data-ttu-id="e0464-116">您可以在使用字串常值的任何位置使用字串插值。</span><span class="sxs-lookup"><span data-stu-id="e0464-116">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="e0464-117">每次執行含有字串插值的程式碼時，都會評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="e0464-117">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="e0464-118">這可讓您分開定義和評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="e0464-118">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="e0464-119">若要在字串插值中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="e0464-119">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="e0464-120">如需詳細資訊，請參閱＜隱含轉換＞一節。</span><span class="sxs-lookup"><span data-stu-id="e0464-120">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="e0464-121">當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。</span><span class="sxs-lookup"><span data-stu-id="e0464-121">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="e0464-122">下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="e0464-122">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

<span data-ttu-id="e0464-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="e0464-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span></span>  

## <a name="implicit-conversions"></a><span data-ttu-id="e0464-124">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="e0464-124">Implicit Conversions</span></span>  

<span data-ttu-id="e0464-125">有三個來自字串插值的隱含型別轉換：</span><span class="sxs-lookup"><span data-stu-id="e0464-125">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="e0464-126">將字串插值轉換成 @System.String。</span><span class="sxs-lookup"><span data-stu-id="e0464-126">Conversion of an interpolated string to a @System.String.</span></span> <span data-ttu-id="e0464-127">下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="e0464-127">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="e0464-128">例如: </span><span class="sxs-lookup"><span data-stu-id="e0464-128">For example:</span></span>

   <span data-ttu-id="e0464-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="e0464-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span></span>  

   <span data-ttu-id="e0464-130">這是字串解譯的最終結果。</span><span class="sxs-lookup"><span data-stu-id="e0464-130">This is the final result of a string interpretation.</span></span> <span data-ttu-id="e0464-131">所有出現的雙大括弧 ("{{" 和 "}}") 都會轉換成單一大括弧。</span><span class="sxs-lookup"><span data-stu-id="e0464-131">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="e0464-132">將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-132">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="e0464-133">若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。</span><span class="sxs-lookup"><span data-stu-id="e0464-133">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="e0464-134">在您明確或隱含呼叫 @System.Object.ToString 方法以格式化字串之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="e0464-134">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the @System.Object.ToString method.</span></span>  <span data-ttu-id="e0464-135">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="e0464-135">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="e0464-136">下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。</span><span class="sxs-lookup"><span data-stu-id="e0464-136">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="e0464-137">它也會將 <xref:System.IFormattable> 變數傳遞給 @System.Console(System.String) 方法。</span><span class="sxs-lookup"><span data-stu-id="e0464-137">It also passes the <xref:System.IFormattable> variable to the @System.Console(System.String) method.</span></span>

   <span data-ttu-id="e0464-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="e0464-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span></span>  

   <span data-ttu-id="e0464-139">請注意，只能使用反映來檢查字串插值。</span><span class="sxs-lookup"><span data-stu-id="e0464-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="e0464-140">如果將它傳遞至字串格式化方法 (例如 @System.Console.WriteLine(System.String))，則會解析其格式項目並傳回結果字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-140">If it is passed to a string formatting method, such as @System.Console.WriteLine(System.String), its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="e0464-141">將字串插值轉換成 <xref:System.FormattableString> 變數，以代表複合格式字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-141">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="e0464-142">檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="e0464-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span>  <span data-ttu-id="e0464-143"><xref:System.FormattableString> 也包含 <xref:System.FormattableString.ToString> 多載，可讓您產生 @System.Globalization.InvariantCulture 和 @System.Globalization.CurrentCulture 的結果字串。</span><span class="sxs-lookup"><span data-stu-id="e0464-143"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the @System.Globalization.InvariantCulture and @System.Globalization.CurrentCulture.</span></span>  <span data-ttu-id="e0464-144">在您格式化之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="e0464-144">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="e0464-145">所有包含插值運算式會轉換成 {0}、\{1\} 等。</span><span class="sxs-lookup"><span data-stu-id="e0464-145">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="e0464-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="e0464-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span></span>  

## <a name="language-specification"></a><span data-ttu-id="e0464-147">語言規格</span><span class="sxs-lookup"><span data-stu-id="e0464-147">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0464-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0464-148">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
<span data-ttu-id="e0464-149"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e0464-149"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="e0464-150"> [C# 程式設計指南](../../../csharp/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="e0464-150"> [C# Programming Guide](../../../csharp/programming-guide/index.md)</span></span>

