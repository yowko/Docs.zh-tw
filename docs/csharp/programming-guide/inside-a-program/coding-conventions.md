---
title: C# 編碼慣例 - C# 程式設計指南
description: '瞭解 c # 中的編碼慣例。 編碼慣例會建立一致的程式碼外觀，並協助複製、變更和維護程式碼。'
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 772aebff0b8c7aebe7c7d5c7634cd2931f4570b1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301849"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="55954-104">C# 編碼慣例 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="55954-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="55954-105">編碼慣例有下列用途：</span><span class="sxs-lookup"><span data-stu-id="55954-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="55954-106">建立外觀一致的程式碼，讓讀者可以專注於內容，而非版面配置。</span><span class="sxs-lookup"><span data-stu-id="55954-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="55954-107">讓讀者可以依據先前的經驗做出假設，更快速地了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="55954-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="55954-108">有助於複製、變更及維護程式碼。</span><span class="sxs-lookup"><span data-stu-id="55954-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="55954-109">示範 C# 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="55954-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="55954-110">Microsoft 會使用本文中的指導方針來開發範例和檔。</span><span class="sxs-lookup"><span data-stu-id="55954-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="55954-111">命名規範</span><span class="sxs-lookup"><span data-stu-id="55954-111">Naming Conventions</span></span>  
  
- <span data-ttu-id="55954-112">在不包含 [using 指示詞](../../language-reference/keywords/using-directive.md)的簡短範例中，使用命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="55954-112">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="55954-113">如果您知道專案中預設會匯入命名空間，則無須完整限定該命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="55954-113">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="55954-114">如果限定的名稱太長無法顯示在同一行，則可以在點 (.) 之後中斷名稱，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="55954-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="55954-115">您無須變更使用 Visual Studio 設計工具所建立的物件之名稱，使其符合其他指導方針。</span><span class="sxs-lookup"><span data-stu-id="55954-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="55954-116">版面配置慣例</span><span class="sxs-lookup"><span data-stu-id="55954-116">Layout Conventions</span></span>  

<span data-ttu-id="55954-117">好的版面配置使用格式設定，來強調程式碼的結構，並讓程式碼更易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="55954-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="55954-118">Microsoft 範例遵循以下慣例：</span><span class="sxs-lookup"><span data-stu-id="55954-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="55954-119">使用預設程式碼編輯器設定 (智慧型縮排、四個字元縮排、定位點儲存為空格)。</span><span class="sxs-lookup"><span data-stu-id="55954-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="55954-120">如需詳細資訊，請參閱[選項、文字編輯器、C#、格式](/visualstudio/ide/reference/options-text-editor-csharp-formatting)。</span><span class="sxs-lookup"><span data-stu-id="55954-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="55954-121">每行只撰寫一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="55954-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="55954-122">每行只撰寫一個宣告。</span><span class="sxs-lookup"><span data-stu-id="55954-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="55954-123">如果連續行不會自動縮排，則縮排一個定位停駐點 (四個空格)。</span><span class="sxs-lookup"><span data-stu-id="55954-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="55954-124">在方法定義與屬性定義之間新增至少一個空白行。</span><span class="sxs-lookup"><span data-stu-id="55954-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="55954-125">使用括號清楚分隔運算式中的子句，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="55954-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="55954-126">註解慣例</span><span class="sxs-lookup"><span data-stu-id="55954-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="55954-127">將註解置於單獨的一行，不在程式碼行結尾處。</span><span class="sxs-lookup"><span data-stu-id="55954-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="55954-128">以大寫字母開始註解文字。</span><span class="sxs-lookup"><span data-stu-id="55954-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="55954-129">以句號結束註解文字。</span><span class="sxs-lookup"><span data-stu-id="55954-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="55954-130">註解分隔符號 (//) 與註解文字之間插入一個空格，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="55954-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="55954-131">不要在註解周圍建立格式化的星號區塊。</span><span class="sxs-lookup"><span data-stu-id="55954-131">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="55954-132">語言指導方針</span><span class="sxs-lookup"><span data-stu-id="55954-132">Language Guidelines</span></span>  

<span data-ttu-id="55954-133">下列各節說明 C# 小組在準備程式碼範例時應遵循的作法。</span><span class="sxs-lookup"><span data-stu-id="55954-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="55954-134">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="55954-134">String Data Type</span></span>  
  
- <span data-ttu-id="55954-135">使用[字串內插補點](../../language-reference/tokens/interpolated.md)串連短字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="55954-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="55954-136">若要在迴圈中附加字串，特別是正在使用大量文字時，請使用 <xref:System.Text.StringBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="55954-136">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="55954-137">隱含類型區域變數</span><span class="sxs-lookup"><span data-stu-id="55954-137">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="55954-138">如果區域變數的類型明顯來自指派的右側，或精確類型並不重要，請針對該變數使用[隱含類型](../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="55954-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="55954-139">當類型不是明顯來自指派的右側時，請不要使用 [var](../../language-reference/keywords/var.md)。</span><span class="sxs-lookup"><span data-stu-id="55954-139">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="55954-140">請勿依賴變數名稱，指定變數的類型。</span><span class="sxs-lookup"><span data-stu-id="55954-140">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="55954-141">有可能會不正確。</span><span class="sxs-lookup"><span data-stu-id="55954-141">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="55954-142">避免使用 `var` 取代 [dynamic](../../language-reference/builtin-types/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="55954-142">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="55954-143">在[for](../../language-reference/keywords/for.md)迴圈中，使用隱含類型來判斷迴圈變數的型別。</span><span class="sxs-lookup"><span data-stu-id="55954-143">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="55954-144">下列範例在 `for` 陳述式中使用隱含類型。</span><span class="sxs-lookup"><span data-stu-id="55954-144">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="55954-145">請勿使用隱含類型來判斷[foreach](../../language-reference/keywords/foreach-in.md)迴圈中迴圈變數的類型。</span><span class="sxs-lookup"><span data-stu-id="55954-145">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="55954-146">下列範例會在語句中使用明確類型 `foreach` 。</span><span class="sxs-lookup"><span data-stu-id="55954-146">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="55954-147">請小心不要不小心變更可反復執行集合的元素類型。</span><span class="sxs-lookup"><span data-stu-id="55954-147">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="55954-148">例如， <xref:System.Linq.IQueryable?displayProperty=nameWithType> 在語句中，從切換到會 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> `foreach` 變更查詢的執行，是很容易的。</span><span class="sxs-lookup"><span data-stu-id="55954-148">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="55954-149">不帶正負號的資料類型</span><span class="sxs-lookup"><span data-stu-id="55954-149">Unsigned Data Type</span></span>  
  
<span data-ttu-id="55954-150">一般而言，請使用 `int` 而非不帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="55954-150">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="55954-151">`int` 的使用在 C# 中非常普遍，當您使用 `int` 時，可更易於與其他程式庫互動。</span><span class="sxs-lookup"><span data-stu-id="55954-151">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="55954-152">陣列</span><span class="sxs-lookup"><span data-stu-id="55954-152">Arrays</span></span>  
  
<span data-ttu-id="55954-153">當您在宣告行上初始化陣列時，請使用簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="55954-153">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="55954-154">委派</span><span class="sxs-lookup"><span data-stu-id="55954-154">Delegates</span></span>  
  
<span data-ttu-id="55954-155">您可以使用簡潔的語法，建立委派類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="55954-155">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="55954-156">例外狀況處理中的 try-catch 和 using 陳述式</span><span class="sxs-lookup"><span data-stu-id="55954-156">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="55954-157">針對大部分例外狀況處理，請使用 [try-catch](../../language-reference/keywords/try-catch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="55954-157">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="55954-158">使用 C# [using 陳述式](../../language-reference/keywords/using-statement.md)，可簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="55954-158">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="55954-159">如果您有 [try-finally](../../language-reference/keywords/try-finally.md) 陳述式，而其中 `finally` 區塊內唯一的程式碼是 <xref:System.IDisposable.Dispose%2A> 方法的呼叫，則請改用 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="55954-159">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="55954-160">&& 和 &#124;&#124; 運算子</span><span class="sxs-lookup"><span data-stu-id="55954-160">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="55954-161">若要避免例外狀況並藉由略過不必要的比較來提升效能，請使用， [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) 而不是在 [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) 執行比較時[&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) ，而不是[&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="55954-161">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="55954-162">New 運算子</span><span class="sxs-lookup"><span data-stu-id="55954-162">New Operator</span></span>  
  
- <span data-ttu-id="55954-163">使用物件執行個體化的簡潔形式，搭配隱含類型，如下宣告所示。</span><span class="sxs-lookup"><span data-stu-id="55954-163">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="55954-164">前一行相當於下列宣告。</span><span class="sxs-lookup"><span data-stu-id="55954-164">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="55954-165">使用物件初始設定式，簡化物件的建立。</span><span class="sxs-lookup"><span data-stu-id="55954-165">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="55954-166">事件處理</span><span class="sxs-lookup"><span data-stu-id="55954-166">Event Handling</span></span>  
  
<span data-ttu-id="55954-167">如果要定義稍後不需要移除的事件處理常式，請使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="55954-167">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="55954-168">靜態成員</span><span class="sxs-lookup"><span data-stu-id="55954-168">Static Members</span></span>  
  
<span data-ttu-id="55954-169">使用類別名稱 *ClassName.StaticMember*，呼叫 [static](../../language-reference/keywords/static.md) 成員。</span><span class="sxs-lookup"><span data-stu-id="55954-169">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="55954-170">這種作法可讓靜態存取更加清晰，從而讓程式碼更易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="55954-170">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="55954-171">請勿使用衍生類別的名稱，限定在基底類別中定義的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="55954-171">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="55954-172">編譯該程式碼時，如果將具有相同名稱的靜態成員加入衍生類別，則會破壞程式碼的清楚程度，且程式碼之後可能會在中斷。</span><span class="sxs-lookup"><span data-stu-id="55954-172">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="55954-173">LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="55954-173">LINQ Queries</span></span>  
  
- <span data-ttu-id="55954-174">請為查詢變數使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="55954-174">Use meaningful names for query variables.</span></span> <span data-ttu-id="55954-175">下列範例對位於西雅圖的客戶，使用 `seattleCustomers`。</span><span class="sxs-lookup"><span data-stu-id="55954-175">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="55954-176">使用別名，確保匿名類型的屬性名稱使用 Pascal 大小寫慣例，大寫正確。</span><span class="sxs-lookup"><span data-stu-id="55954-176">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="55954-177">當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="55954-177">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="55954-178">例如，如果查詢傳回了客戶名稱與經銷商 ID，但沒有在結果在將它們保留為 `Name` 和 `ID`，請對它們重新命名，以釐清 `Name` 是客戶的名稱，而 `ID` 是經銷商的 ID。</span><span class="sxs-lookup"><span data-stu-id="55954-178">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="55954-179">在查詢變數和範圍變數的宣告中使用隱含類型。</span><span class="sxs-lookup"><span data-stu-id="55954-179">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="55954-180">在 [from](../../language-reference/keywords/from-clause.md) 子句下對齊查詢子句，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="55954-180">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="55954-181">在其他查詢子句前，使用 [where](../../language-reference/keywords/where-clause.md) 子句以確保之後的查詢子句，會對已經過篩選而減少數量的一組資料進行操作。</span><span class="sxs-lookup"><span data-stu-id="55954-181">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="55954-182">使用多個 `from` 子句來存取內部集合，而非使用 [join](../../language-reference/keywords/join-clause.md) 子句。</span><span class="sxs-lookup"><span data-stu-id="55954-182">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="55954-183">例如，`Student` 物件的集合可能每一個都包含測驗分數的集合。</span><span class="sxs-lookup"><span data-stu-id="55954-183">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="55954-184">執行下列查詢時，會傳回每個超過 90 的分數，以及取得該分數的學生姓氏。</span><span class="sxs-lookup"><span data-stu-id="55954-184">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="55954-185">安全性</span><span class="sxs-lookup"><span data-stu-id="55954-185">Security</span></span>  

<span data-ttu-id="55954-186">請遵循[安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)中的指引。</span><span class="sxs-lookup"><span data-stu-id="55954-186">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55954-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55954-187">See also</span></span>

- [<span data-ttu-id="55954-188">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="55954-188">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="55954-189">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="55954-189">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
