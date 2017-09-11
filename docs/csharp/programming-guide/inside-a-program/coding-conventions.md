---
title: "C# 編碼慣例 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f32fdc0eb1954cdac30c39e05c74d43301d850c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="2a0df-102">C# 編碼慣例 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2a0df-102">C# Coding Conventions (C# Programming Guide)</span></span>
<span data-ttu-id="2a0df-103">[C# 語言規格](http://go.microsoft.com/fwlink/?LinkId=199552)不會定義編碼標準。</span><span class="sxs-lookup"><span data-stu-id="2a0df-103">The [C# Language Specification](http://go.microsoft.com/fwlink/?LinkId=199552) does not define a coding standard.</span></span> <span data-ttu-id="2a0df-104">但 Microsoft 會利用本主題中的指導方針，開發範例與文件。</span><span class="sxs-lookup"><span data-stu-id="2a0df-104">However, the guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
 <span data-ttu-id="2a0df-105">編碼慣例有下列用途：</span><span class="sxs-lookup"><span data-stu-id="2a0df-105">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="2a0df-106">建立外觀一致的程式碼，讓讀者可以專注於內容，而非版面配置。</span><span class="sxs-lookup"><span data-stu-id="2a0df-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="2a0df-107">讓讀者可以依據先前的經驗做出假設，更快速地了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a0df-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="2a0df-108">有助於複製、變更及維護程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a0df-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="2a0df-109">示範 C# 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="2a0df-109">They demonstrate C# best practices.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="2a0df-110">命名規範</span><span class="sxs-lookup"><span data-stu-id="2a0df-110">Naming Conventions</span></span>  
  
-   <span data-ttu-id="2a0df-111">在不包含 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)的簡短範例中，使用命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="2a0df-111">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="2a0df-112">如果您知道專案中預設會匯入命名空間，則無須完整限定該命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a0df-112">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="2a0df-113">如果限定的名稱太長無法顯示在同一行，則可以在點 (.) 之後中斷名稱，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-113">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     <span data-ttu-id="2a0df-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-115">您無須變更使用 Visual Studio 設計工具所建立的物件之名稱，使其符合其他指導方針。</span><span class="sxs-lookup"><span data-stu-id="2a0df-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="2a0df-116">版面配置慣例</span><span class="sxs-lookup"><span data-stu-id="2a0df-116">Layout Conventions</span></span>  
 <span data-ttu-id="2a0df-117">好的版面配置使用格式設定，來強調程式碼的結構，並讓程式碼更易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="2a0df-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="2a0df-118">Microsoft 範例遵循以下慣例：</span><span class="sxs-lookup"><span data-stu-id="2a0df-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="2a0df-119">使用預設程式碼編輯器設定 (智慧型縮排、四個字元縮排、定位點儲存為空格)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="2a0df-120">如需詳細資訊，請參閱[選項、文字編輯器、C#、格式](/visualstudio/ide/reference/options-text-editor-csharp-formatting)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="2a0df-121">每行只撰寫一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a0df-121">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="2a0df-122">每行只撰寫一個宣告。</span><span class="sxs-lookup"><span data-stu-id="2a0df-122">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="2a0df-123">如果連續行不會自動縮排，則縮排一個定位停駐點 (四個空格)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="2a0df-124">在方法定義與屬性定義之間新增至少一個空白行。</span><span class="sxs-lookup"><span data-stu-id="2a0df-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="2a0df-125">使用括號清楚分隔運算式中的子句，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     <span data-ttu-id="2a0df-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="2a0df-127">註解慣例</span><span class="sxs-lookup"><span data-stu-id="2a0df-127">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="2a0df-128">將註解置於單獨的一行，不在程式碼行結尾處。</span><span class="sxs-lookup"><span data-stu-id="2a0df-128">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="2a0df-129">以大寫字母開始註解文字。</span><span class="sxs-lookup"><span data-stu-id="2a0df-129">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="2a0df-130">以句號結束註解文字。</span><span class="sxs-lookup"><span data-stu-id="2a0df-130">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="2a0df-131">註解分隔符號 (//) 與註解文字之間插入一個空格，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-131">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     <span data-ttu-id="2a0df-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-133">不要在註解周圍建立格式化的星號區塊。</span><span class="sxs-lookup"><span data-stu-id="2a0df-133">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="2a0df-134">語言指導方針</span><span class="sxs-lookup"><span data-stu-id="2a0df-134">Language Guidelines</span></span>  
 <span data-ttu-id="2a0df-135">下列各節說明 C# 小組在準備程式碼範例時應遵循的作法。</span><span class="sxs-lookup"><span data-stu-id="2a0df-135">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="2a0df-136">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="2a0df-136">String Data Type</span></span>  
  
-   <span data-ttu-id="2a0df-137">使用 `+` 運算子串連短字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-137">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     <span data-ttu-id="2a0df-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-139">若要在迴圈中附加字串，特別是正在使用大量文字時，請使用 <xref:System.Text.StringBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="2a0df-139">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="2a0df-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span></span>  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="2a0df-141">隱含類型區域變數</span><span class="sxs-lookup"><span data-stu-id="2a0df-141">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="2a0df-142">如果區域變數的類型明顯來自指派的右側，或精確類型並不重要，請針對該變數使用[隱含類型](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-142">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     <span data-ttu-id="2a0df-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-144">當類型不是明顯來自指派的右側時，請不要使用 [var](../../../csharp/language-reference/keywords/var.md)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-144">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     <span data-ttu-id="2a0df-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-146">請勿依賴變數名稱，指定變數的類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-146">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="2a0df-147">有可能會不正確。</span><span class="sxs-lookup"><span data-stu-id="2a0df-147">It might not be correct.</span></span>  
  
     <span data-ttu-id="2a0df-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-149">避免使用 `var` 取代 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)。</span><span class="sxs-lookup"><span data-stu-id="2a0df-149">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="2a0df-150">使用隱含類型，確定 [for](../../../csharp/language-reference/keywords/for.md) 和 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 迴圈中迴圈變數的類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-150">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="2a0df-151">下列範例在 `for` 陳述式中使用隱含類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-151">The following example uses implicit typing in a `for` statement.</span></span>  
  
     <span data-ttu-id="2a0df-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span></span>  
  
     <span data-ttu-id="2a0df-153">下列範例在 `foreach` 陳述式中使用隱含類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-153">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     <span data-ttu-id="2a0df-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="2a0df-155">不帶正負號的資料類型</span><span class="sxs-lookup"><span data-stu-id="2a0df-155">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="2a0df-156">一般而言，請使用 `int` 而非不帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="2a0df-157">`int` 的使用在 C# 中非常普遍，當您使用 `int` 時，可更易於與其他程式庫互動。</span><span class="sxs-lookup"><span data-stu-id="2a0df-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="2a0df-158">陣列</span><span class="sxs-lookup"><span data-stu-id="2a0df-158">Arrays</span></span>  
  
-   <span data-ttu-id="2a0df-159">當您在宣告行上初始化陣列時，請使用簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="2a0df-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     <span data-ttu-id="2a0df-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span></span>  
  
### <a name="delegates"></a><span data-ttu-id="2a0df-161">委派</span><span class="sxs-lookup"><span data-stu-id="2a0df-161">Delegates</span></span>  
  
-   <span data-ttu-id="2a0df-162">您可以使用簡潔的語法，建立委派類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a0df-162">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     <span data-ttu-id="2a0df-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span></span>  
  
     <span data-ttu-id="2a0df-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span></span>  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="2a0df-165">例外狀況處理中的 try-catch 和 using 陳述式</span><span class="sxs-lookup"><span data-stu-id="2a0df-165">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="2a0df-166">針對大部分例外狀況處理，請使用 [try-catch](../../../csharp/language-reference/keywords/try-catch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a0df-166">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     <span data-ttu-id="2a0df-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-168">使用 C# [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)，可簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a0df-168">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="2a0df-169">如果您有 [try-finally](../../../csharp/language-reference/keywords/try-finally.md) 陳述式，而其中 `finally` 區塊內唯一的程式碼是 <xref:System.IDisposable.Dispose%2A> 方法的呼叫，則請改用 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a0df-169">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     <span data-ttu-id="2a0df-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span></span>  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="2a0df-171">&& 和 &#124;&#124; 運算子</span><span class="sxs-lookup"><span data-stu-id="2a0df-171">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="2a0df-172">為避免發生例外狀況，並略過不必要的比較來提升效能，請在執行比較時使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 而非 [&](../../../csharp/language-reference/operators/and-operator.md)，並使用 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 而非 [&#124;](../../../csharp/language-reference/operators/or-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-172">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     <span data-ttu-id="2a0df-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span></span>  
  
### <a name="new-operator"></a><span data-ttu-id="2a0df-174">New 運算子</span><span class="sxs-lookup"><span data-stu-id="2a0df-174">New Operator</span></span>  
  
-   <span data-ttu-id="2a0df-175">使用物件執行個體化的簡潔形式，搭配隱含類型，如下宣告所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-175">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     <span data-ttu-id="2a0df-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span></span>  
  
     <span data-ttu-id="2a0df-177">前一行相當於下列宣告。</span><span class="sxs-lookup"><span data-stu-id="2a0df-177">The previous line is equivalent to the following declaration.</span></span>  
  
     <span data-ttu-id="2a0df-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-179">使用物件初始設定式，簡化物件的建立。</span><span class="sxs-lookup"><span data-stu-id="2a0df-179">Use object initializers to simplify object creation.</span></span>  
  
     <span data-ttu-id="2a0df-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="2a0df-181">事件處理</span><span class="sxs-lookup"><span data-stu-id="2a0df-181">Event Handling</span></span>  
  
-   <span data-ttu-id="2a0df-182">如果要定義稍後不需要移除的事件處理常式，請使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="2a0df-182">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     <span data-ttu-id="2a0df-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span></span>  
  
     <span data-ttu-id="2a0df-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span></span>  
  
### <a name="static-members"></a><span data-ttu-id="2a0df-185">靜態成員</span><span class="sxs-lookup"><span data-stu-id="2a0df-185">Static Members</span></span>  
  
-   <span data-ttu-id="2a0df-186">使用類別名稱 *ClassName.StaticMember*，呼叫 [static](../../../csharp/language-reference/keywords/static.md) 成員。</span><span class="sxs-lookup"><span data-stu-id="2a0df-186">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="2a0df-187">這種作法可讓靜態存取更加清晰，從而讓程式碼更易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="2a0df-187">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="2a0df-188">請勿使用衍生類別的名稱，限定在基底類別中定義的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="2a0df-188">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="2a0df-189">編譯該程式碼時，如果將具有相同名稱的靜態成員加入衍生類別，則會破壞程式碼的清楚程度，且程式碼之後可能會在中斷。</span><span class="sxs-lookup"><span data-stu-id="2a0df-189">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="2a0df-190">LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="2a0df-190">LINQ Queries</span></span>  
  
-   <span data-ttu-id="2a0df-191">請為查詢變數使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a0df-191">Use meaningful names for query variables.</span></span> <span data-ttu-id="2a0df-192">下列範例對位於西雅圖的客戶，使用 `seattleCustomers`。</span><span class="sxs-lookup"><span data-stu-id="2a0df-192">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     <span data-ttu-id="2a0df-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-194">使用別名，確保匿名類型的屬性名稱使用 Pascal 大小寫慣例，大寫正確。</span><span class="sxs-lookup"><span data-stu-id="2a0df-194">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     <span data-ttu-id="2a0df-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-196">當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="2a0df-196">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="2a0df-197">例如，如果查詢傳回了客戶名稱與經銷商 ID，但沒有在結果在將它們保留為 `Name` 和 `ID`，請對它們重新命名，以釐清 `Name` 是客戶的名稱，而 `ID` 是經銷商的 ID。</span><span class="sxs-lookup"><span data-stu-id="2a0df-197">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     <span data-ttu-id="2a0df-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-199">在查詢變數和範圍變數的宣告中使用隱含類型。</span><span class="sxs-lookup"><span data-stu-id="2a0df-199">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     <span data-ttu-id="2a0df-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-201">在 [from](../../../csharp/language-reference/keywords/from-clause.md) 子句下對齊查詢子句，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a0df-201">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="2a0df-202">在其他查詢子句前，使用 [where](../../../csharp/language-reference/keywords/where-clause.md) 子句以確保之後的查詢子句，會對已經過篩選而減少數量的一組資料進行操作。</span><span class="sxs-lookup"><span data-stu-id="2a0df-202">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     <span data-ttu-id="2a0df-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span></span>  
  
-   <span data-ttu-id="2a0df-204">使用多個 `from` 子句來存取內部集合，而非使用 [join](../../../csharp/language-reference/keywords/join-clause.md) 子句。</span><span class="sxs-lookup"><span data-stu-id="2a0df-204">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="2a0df-205">例如，`Student` 物件的集合可能每一個都包含測驗分數的集合。</span><span class="sxs-lookup"><span data-stu-id="2a0df-205">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="2a0df-206">執行下列查詢時，會傳回每個超過 90 的分數，以及取得該分數的學生姓氏。</span><span class="sxs-lookup"><span data-stu-id="2a0df-206">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     <span data-ttu-id="2a0df-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span><span class="sxs-lookup"><span data-stu-id="2a0df-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="2a0df-208">安全性</span><span class="sxs-lookup"><span data-stu-id="2a0df-208">Security</span></span>  
 <span data-ttu-id="2a0df-209">請遵循[安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)中的指引。</span><span class="sxs-lookup"><span data-stu-id="2a0df-209">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0df-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a0df-210">See Also</span></span>  
 <span data-ttu-id="2a0df-211">[Visual Basic 編碼慣例](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="2a0df-211">[Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span></span>  
 [<span data-ttu-id="2a0df-212">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="2a0df-212">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)

