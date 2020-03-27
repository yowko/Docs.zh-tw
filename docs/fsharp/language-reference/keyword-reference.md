---
title: 關鍵字參考
description: 查找有關所有 F# 語言關鍵字的資訊的連結。
f1_keywords:
- new_FS
- use_FS
- end_FS
- lsl_FS
- exception_FS
- asr_FS
- if_FS
- internal_FS
- default_FS
- in_FS
- lsr_FS
- open_FS
- static_FS
- assert_FS
- match_FS
- land_FS
- with_FS
- inherit_FS
- mutable_FS
- downto_FS
- false_FS
- sig_FS
- and_FS
- true_FS
- namespace_FS
- public_FS
- lxor_FS
- val_FS
- void_FS
- downcast_FS
- function_FS
- while_FS
- for_FS
- class_FS
- done_FS
- to_FS
- module_FS
- let_FS
- delegate_FS
- abstract_FS
- then_FS
- when_FS
- lazy_FS
- try_FS
- inline_FS
- do_FS
- upcast_FS
- begin_FS
- base_FS
- fun_FS
- struct_FS
- as_FS
- extern_FS
- null_FS
- lor_FS
- return_FS
- mod_FS
- private_FS
- of_FS
- or_FS
- member_FS
- type_FS
- rec_FS
- elif_FS
- override_FS
- interface_FS
- yield_FS
- else_FS
- finally_FS
- global_FS
- select_FS
- use!_FS
dev_langs:
- FSharp
ms.date: 11/04/2019
ms.openlocfilehash: 34959f471406643e85990c2c80a38a684759a7f9
ms.sourcegitcommit: b16eacb6f94a5b601882a861ad17cc5470a8d5d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80352313"
---
# <a name="keyword-reference"></a><span data-ttu-id="114df-103">關鍵字參考</span><span class="sxs-lookup"><span data-stu-id="114df-103">Keyword Reference</span></span>

<span data-ttu-id="114df-104">本主題包含有關所有 F# 語言關鍵字的資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="114df-104">This topic contains links to information about all F# language keywords.</span></span>

## <a name="f-keyword-table"></a><span data-ttu-id="114df-105">F# 關鍵字表</span><span class="sxs-lookup"><span data-stu-id="114df-105">F# Keyword Table</span></span>

<span data-ttu-id="114df-106">下表按字母順序顯示所有 F# 關鍵字，以及包含詳細資訊的相關主題的簡短說明和連結。</span><span class="sxs-lookup"><span data-stu-id="114df-106">The following table shows all F# keywords in alphabetical order, together with brief descriptions and links to relevant topics that contain more information.</span></span>

|<span data-ttu-id="114df-107">關鍵字</span><span class="sxs-lookup"><span data-stu-id="114df-107">Keyword</span></span>|<span data-ttu-id="114df-108">連結</span><span class="sxs-lookup"><span data-stu-id="114df-108">Link</span></span>|<span data-ttu-id="114df-109">描述</span><span class="sxs-lookup"><span data-stu-id="114df-109">Description</span></span>|
|-------|----|-----------|
|`abstract`|[<span data-ttu-id="114df-110">成員</span><span class="sxs-lookup"><span data-stu-id="114df-110">Members</span></span>](./members/index.md)<br /><br />[<span data-ttu-id="114df-111">抽象類別</span><span class="sxs-lookup"><span data-stu-id="114df-111">Abstract Classes</span></span>](abstract-classes.md)|<span data-ttu-id="114df-112">指示在聲明該方法的類型中沒有實現的方法，或者它是虛擬的並且具有預設實現的方法。</span><span class="sxs-lookup"><span data-stu-id="114df-112">Indicates a method that either has no implementation in the type in which it is declared or that is virtual and has a default implementation.</span></span>|
|`and`|[<span data-ttu-id="114df-113">`let`綁定</span><span class="sxs-lookup"><span data-stu-id="114df-113">`let` Bindings</span></span>](./functions/let-bindings.md)<br /><br />[<span data-ttu-id="114df-114">記錄</span><span class="sxs-lookup"><span data-stu-id="114df-114">Records</span></span>](records.md)<br /><br />[<span data-ttu-id="114df-115">成員</span><span class="sxs-lookup"><span data-stu-id="114df-115">Members</span></span>](./members/index.md)<br /><br />[<span data-ttu-id="114df-116">約束</span><span class="sxs-lookup"><span data-stu-id="114df-116">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-117">用於相互遞迴綁定和記錄、屬性聲明中以及泛型參數的多個約束。</span><span class="sxs-lookup"><span data-stu-id="114df-117">Used in mutually recursive bindings and records, in property declarations, and with multiple constraints on generic parameters.</span></span>|
|`as`|[<span data-ttu-id="114df-118">類別</span><span class="sxs-lookup"><span data-stu-id="114df-118">Classes</span></span>](classes.md)<br /><br />[<span data-ttu-id="114df-119">模式比對</span><span class="sxs-lookup"><span data-stu-id="114df-119">Pattern Matching</span></span>](Pattern-Matching.md)|<span data-ttu-id="114df-120">用於為當前類物件指定物件名稱。</span><span class="sxs-lookup"><span data-stu-id="114df-120">Used to give the current class object an object name.</span></span> <span data-ttu-id="114df-121">還用於在模式匹配中為整個模式指定名稱。</span><span class="sxs-lookup"><span data-stu-id="114df-121">Also used to give a name to a whole pattern within a pattern match.</span></span>|
|`assert`|[<span data-ttu-id="114df-122">判斷提示</span><span class="sxs-lookup"><span data-stu-id="114df-122">Assertions</span></span>](assertions.md)|<span data-ttu-id="114df-123">用於在調試期間驗證代碼。</span><span class="sxs-lookup"><span data-stu-id="114df-123">Used to verify code during debugging.</span></span>|
|`base`|[<span data-ttu-id="114df-124">類別</span><span class="sxs-lookup"><span data-stu-id="114df-124">Classes</span></span>](classes.md)<br /><br />[<span data-ttu-id="114df-125">繼承</span><span class="sxs-lookup"><span data-stu-id="114df-125">Inheritance</span></span>](inheritance.md)|<span data-ttu-id="114df-126">用作基類物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="114df-126">Used as the name of the base class object.</span></span>|
|`begin`|[<span data-ttu-id="114df-127">詳細語法</span><span class="sxs-lookup"><span data-stu-id="114df-127">Verbose Syntax</span></span>](verbose-syntax.md)|<span data-ttu-id="114df-128">在詳細語法中，指示代碼塊的開始。</span><span class="sxs-lookup"><span data-stu-id="114df-128">In verbose syntax, indicates the start of a code block.</span></span>|
|`class`|[<span data-ttu-id="114df-129">類別</span><span class="sxs-lookup"><span data-stu-id="114df-129">Classes</span></span>](classes.md)|<span data-ttu-id="114df-130">在詳細語法中，指示類定義的開始。</span><span class="sxs-lookup"><span data-stu-id="114df-130">In verbose syntax, indicates the start of a class definition.</span></span>|
|`default`|[<span data-ttu-id="114df-131">成員</span><span class="sxs-lookup"><span data-stu-id="114df-131">Members</span></span>](./members/index.md)|<span data-ttu-id="114df-132">指示抽象方法的實現;與抽象方法聲明一起使用以創建虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="114df-132">Indicates an implementation of an abstract method; used together with an abstract method declaration to create a virtual method.</span></span>|
|`delegate`|[<span data-ttu-id="114df-133">委派</span><span class="sxs-lookup"><span data-stu-id="114df-133">Delegates</span></span>](delegates.md)|<span data-ttu-id="114df-134">用於聲明委託。</span><span class="sxs-lookup"><span data-stu-id="114df-134">Used to declare a delegate.</span></span>|
|`do`|[<span data-ttu-id="114df-135">do 繫結</span><span class="sxs-lookup"><span data-stu-id="114df-135">do Bindings</span></span>](./functions/do-bindings.md)<br /><br />[<span data-ttu-id="114df-136">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-136">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)<br /><br />[<span data-ttu-id="114df-137">迴圈：`for...in` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-137">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)<br /><br />[<span data-ttu-id="114df-138">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-138">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)|<span data-ttu-id="114df-139">用於迴圈構造或執行命令代碼。</span><span class="sxs-lookup"><span data-stu-id="114df-139">Used in looping constructs or to execute imperative code.</span></span>|
|`done`|[<span data-ttu-id="114df-140">詳細語法</span><span class="sxs-lookup"><span data-stu-id="114df-140">Verbose Syntax</span></span>](verbose-syntax.md)|<span data-ttu-id="114df-141">在詳細語法中，指示迴圈運算式中代碼塊的結束。</span><span class="sxs-lookup"><span data-stu-id="114df-141">In verbose syntax, indicates the end of a block of code in a looping expression.</span></span>|
|`downcast`|[<span data-ttu-id="114df-142">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="114df-142">Casting and Conversions</span></span>](casting-and-conversions.md)|<span data-ttu-id="114df-143">用於轉換為繼承鏈中較低的類型。</span><span class="sxs-lookup"><span data-stu-id="114df-143">Used to convert to a type that is lower in the inheritance chain.</span></span>|
|`downto`|[<span data-ttu-id="114df-144">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-144">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)|<span data-ttu-id="114df-145">在運算式`for`中，在反向計數時使用。</span><span class="sxs-lookup"><span data-stu-id="114df-145">In a `for` expression, used when counting in reverse.</span></span>|
|`elif`|[<span data-ttu-id="114df-146">條件運算式：`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="114df-146">Conditional Expressions: `if...then...else`</span></span>](conditional-expressions-if-then-else.md)|<span data-ttu-id="114df-147">用於條件分支。</span><span class="sxs-lookup"><span data-stu-id="114df-147">Used in conditional branching.</span></span> <span data-ttu-id="114df-148">短形式的`else if`.</span><span class="sxs-lookup"><span data-stu-id="114df-148">A short form of `else if`.</span></span>|
|`else`|[<span data-ttu-id="114df-149">條件運算式：`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="114df-149">Conditional Expressions: `if...then...else`</span></span>](conditional-expressions-if-then-else.md)|<span data-ttu-id="114df-150">用於條件分支。</span><span class="sxs-lookup"><span data-stu-id="114df-150">Used in conditional branching.</span></span>|
|`end`|[<span data-ttu-id="114df-151">結構</span><span class="sxs-lookup"><span data-stu-id="114df-151">Structures</span></span>](structures.md)<br /><br />[<span data-ttu-id="114df-152">差別聯集</span><span class="sxs-lookup"><span data-stu-id="114df-152">Discriminated Unions</span></span>](discriminated-unions.md)<br /><br />[<span data-ttu-id="114df-153">記錄</span><span class="sxs-lookup"><span data-stu-id="114df-153">Records</span></span>](records.md)<br /><br />[<span data-ttu-id="114df-154">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="114df-154">Type Extensions</span></span>](type-extensions.md)<br /><br />[<span data-ttu-id="114df-155">詳細語法</span><span class="sxs-lookup"><span data-stu-id="114df-155">Verbose Syntax</span></span>](verbose-syntax.md)|<span data-ttu-id="114df-156">在類型定義和類型擴展中，指示成員定義部分的末尾。</span><span class="sxs-lookup"><span data-stu-id="114df-156">In type definitions and type extensions, indicates the end of a section of member definitions.</span></span><br /><br /><span data-ttu-id="114df-157">在詳細語法中，用於指定以`begin`關鍵字開頭的代碼塊的末尾。</span><span class="sxs-lookup"><span data-stu-id="114df-157">In verbose syntax, used to specify the end of a code block that starts with the `begin` keyword.</span></span>|
|`exception`|[<span data-ttu-id="114df-158">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="114df-158">Exception Handling</span></span>](./exception-handling/index.md)<br /><br />[<span data-ttu-id="114df-159">異常類型</span><span class="sxs-lookup"><span data-stu-id="114df-159">Exception Types</span></span>](./exception-handling/exception-types.md)|<span data-ttu-id="114df-160">用於聲明異常類型。</span><span class="sxs-lookup"><span data-stu-id="114df-160">Used to declare an exception type.</span></span>|
|`extern`|[<span data-ttu-id="114df-161">外部函式</span><span class="sxs-lookup"><span data-stu-id="114df-161">External Functions</span></span>](./functions/external-functions.md)|<span data-ttu-id="114df-162">指示聲明的程式元素在另一個二進位或程式集中定義。</span><span class="sxs-lookup"><span data-stu-id="114df-162">Indicates that a declared program element is defined in another binary or assembly.</span></span>|
|`false`|[<span data-ttu-id="114df-163">基本類型</span><span class="sxs-lookup"><span data-stu-id="114df-163">Primitive Types</span></span>](basic-types.md)|<span data-ttu-id="114df-164">用作布林文本。</span><span class="sxs-lookup"><span data-stu-id="114df-164">Used as a Boolean literal.</span></span>|
|`finally`|[<span data-ttu-id="114df-165">例外狀況：`try...finally` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-165">Exceptions: The `try...finally` Expression</span></span>](./exception-handling/the-try-finally-expression.md)|<span data-ttu-id="114df-166">與一起使用`try`，以引入執行的代碼塊，而不考慮是否發生異常。</span><span class="sxs-lookup"><span data-stu-id="114df-166">Used together with `try` to introduce a block of code that executes regardless of whether an exception occurs.</span></span>|
|`fixed`|[<span data-ttu-id="114df-167">固定</span><span class="sxs-lookup"><span data-stu-id="114df-167">Fixed</span></span>](fixed.md)|<span data-ttu-id="114df-168">用於在堆疊上"固定"指標，以防止其被垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="114df-168">Used to "pin" a pointer on the stack to prevent it from being garbage collected.</span></span>|
|`for`|[<span data-ttu-id="114df-169">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-169">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)<br /><br />[<span data-ttu-id="114df-170">迴圈：for...in 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-170">Loops: for...in Expression</span></span>](loops-for-in-expression.md)|<span data-ttu-id="114df-171">用於迴圈構造。</span><span class="sxs-lookup"><span data-stu-id="114df-171">Used in looping constructs.</span></span>|
|`fun`|[<span data-ttu-id="114df-172">蘭姆達運算式：關鍵字`fun`</span><span class="sxs-lookup"><span data-stu-id="114df-172">Lambda Expressions: The `fun` Keyword</span></span>](./functions/lambda-expressions-the-fun-keyword.md)|<span data-ttu-id="114df-173">用於 lambda 運算式，也稱為匿名函數。</span><span class="sxs-lookup"><span data-stu-id="114df-173">Used in lambda expressions, also known as anonymous functions.</span></span>|
|`function`|[<span data-ttu-id="114df-174">比對運算式</span><span class="sxs-lookup"><span data-stu-id="114df-174">Match Expressions</span></span>](match-expressions.md)<br /><br />[<span data-ttu-id="114df-175">蘭姆達運算式：有趣的關鍵字</span><span class="sxs-lookup"><span data-stu-id="114df-175">Lambda Expressions: The fun Keyword</span></span>](./functions/lambda-expressions-the-fun-keyword.md)|<span data-ttu-id="114df-176">用作 lambda 運算式中`fun`關鍵字和`match`運算式的較短替代方法，該運算式在單個參數上具有模式匹配。</span><span class="sxs-lookup"><span data-stu-id="114df-176">Used as a shorter alternative to the `fun` keyword and a `match` expression in a lambda expression that has pattern matching on a single argument.</span></span>|
|`global`|[<span data-ttu-id="114df-177">命名空間</span><span class="sxs-lookup"><span data-stu-id="114df-177">Namespaces</span></span>](namespaces.md)|<span data-ttu-id="114df-178">用於引用頂級 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="114df-178">Used to reference the top-level .NET namespace.</span></span>|
|`if`|[<span data-ttu-id="114df-179">條件運算式：`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="114df-179">Conditional Expressions: `if...then...else`</span></span>](conditional-expressions-if-then-else.md)|<span data-ttu-id="114df-180">用於條件分支構造。</span><span class="sxs-lookup"><span data-stu-id="114df-180">Used in conditional branching constructs.</span></span>|
|`in`|[<span data-ttu-id="114df-181">迴圈：for...in 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-181">Loops: for...in Expression</span></span>](loops-for-in-expression.md)<br /><br />[<span data-ttu-id="114df-182">詳細語法</span><span class="sxs-lookup"><span data-stu-id="114df-182">Verbose Syntax</span></span>](verbose-syntax.md)|<span data-ttu-id="114df-183">用於序列運算式，在詳細語法中用於將運算式與綁定分開。</span><span class="sxs-lookup"><span data-stu-id="114df-183">Used for sequence expressions and, in verbose syntax, to separate expressions from bindings.</span></span>|
|`inherit`|[<span data-ttu-id="114df-184">繼承</span><span class="sxs-lookup"><span data-stu-id="114df-184">Inheritance</span></span>](inheritance.md)|<span data-ttu-id="114df-185">用於指定基類或基介面。</span><span class="sxs-lookup"><span data-stu-id="114df-185">Used to specify a base class or base interface.</span></span>|
|`inline`|[<span data-ttu-id="114df-186">函式</span><span class="sxs-lookup"><span data-stu-id="114df-186">Functions</span></span>](./functions/index.md)<br /><br />[<span data-ttu-id="114df-187">內聯函數</span><span class="sxs-lookup"><span data-stu-id="114df-187">Inline Functions</span></span>](./functions/inline-functions.md)|<span data-ttu-id="114df-188">用於指示應直接集成到調用方代碼中的函數。</span><span class="sxs-lookup"><span data-stu-id="114df-188">Used to indicate a function that should be integrated directly into the caller's code.</span></span>|
|`interface`|[<span data-ttu-id="114df-189">介面</span><span class="sxs-lookup"><span data-stu-id="114df-189">Interfaces</span></span>](interfaces.md)|<span data-ttu-id="114df-190">用於聲明和實現介面。</span><span class="sxs-lookup"><span data-stu-id="114df-190">Used to declare and implement interfaces.</span></span>|
|`internal`|[<span data-ttu-id="114df-191">存取控制</span><span class="sxs-lookup"><span data-stu-id="114df-191">Access Control</span></span>](access-control.md)|<span data-ttu-id="114df-192">用於指定成員在程式集內可見，但不在程式集外部。</span><span class="sxs-lookup"><span data-stu-id="114df-192">Used to specify that a member is visible inside an assembly but not outside it.</span></span>|
|`lazy`|[<span data-ttu-id="114df-193">延遲運算式</span><span class="sxs-lookup"><span data-stu-id="114df-193">Lazy Expressions</span></span>](lazy-expressions.md)|<span data-ttu-id="114df-194">用於指定僅在需要結果時執行的運算式。</span><span class="sxs-lookup"><span data-stu-id="114df-194">Used to specify an expression that is to be performed only when a result is needed.</span></span>|
|`let`|[<span data-ttu-id="114df-195">`let`綁定</span><span class="sxs-lookup"><span data-stu-id="114df-195">`let` Bindings</span></span>](./functions/let-bindings.md)|<span data-ttu-id="114df-196">用於將名稱關聯或綁定到值或函數。</span><span class="sxs-lookup"><span data-stu-id="114df-196">Used to associate, or bind, a name to a value or function.</span></span>|
|`let!`|[<span data-ttu-id="114df-197">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="114df-197">Asynchronous Workflows</span></span>](asynchronous-workflows.md)<br /><br />[<span data-ttu-id="114df-198">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-198">Computation Expressions</span></span>](computation-expressions.md)|<span data-ttu-id="114df-199">在非同步工作流中用於將名稱綁定到非同步計算的結果，或者在其他計算運算式中用於將名稱綁定到結果（該結果屬於計算類型）。</span><span class="sxs-lookup"><span data-stu-id="114df-199">Used in asynchronous workflows to bind a name to the result of an asynchronous computation, or, in other computation expressions, used to bind a name to a result, which is of the computation type.</span></span>|
|`match`|[<span data-ttu-id="114df-200">比對運算式</span><span class="sxs-lookup"><span data-stu-id="114df-200">Match Expressions</span></span>](match-expressions.md)|<span data-ttu-id="114df-201">用於通過將值與模式進行比較進行分支。</span><span class="sxs-lookup"><span data-stu-id="114df-201">Used to branch by comparing a value to a pattern.</span></span>|
|`match!`|[<span data-ttu-id="114df-202">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-202">Computation Expressions</span></span>](computation-expressions.md#match)|<span data-ttu-id="114df-203">用於將調用對計算運算式和模式匹配在其結果上內聯。</span><span class="sxs-lookup"><span data-stu-id="114df-203">Used to inline a call to a computation expression and pattern match on its result.</span></span>|
|`member`|[<span data-ttu-id="114df-204">成員</span><span class="sxs-lookup"><span data-stu-id="114df-204">Members</span></span>](./members/index.md)|<span data-ttu-id="114df-205">用於聲明物件類型中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="114df-205">Used to declare a property or method in an object type.</span></span>|
|`module`|[<span data-ttu-id="114df-206">模組</span><span class="sxs-lookup"><span data-stu-id="114df-206">Modules</span></span>](modules.md)|<span data-ttu-id="114df-207">用於將名稱與一組相關類型、值和函數相關聯，以便從邏輯上將其與其他代碼分開。</span><span class="sxs-lookup"><span data-stu-id="114df-207">Used to associate a name with a group of related types, values, and functions, to logically separate it from other code.</span></span>|
|`mutable`|[<span data-ttu-id="114df-208">let 繫結</span><span class="sxs-lookup"><span data-stu-id="114df-208">let Bindings</span></span>](./functions/let-bindings.md)|<span data-ttu-id="114df-209">用於聲明變數，即可以更改的值。</span><span class="sxs-lookup"><span data-stu-id="114df-209">Used to declare a variable, that is, a value that can be changed.</span></span>|
|`namespace`|[<span data-ttu-id="114df-210">命名空間</span><span class="sxs-lookup"><span data-stu-id="114df-210">Namespaces</span></span>](namespaces.md)|<span data-ttu-id="114df-211">用於將名稱與一組相關類型和模組相關聯，以便從邏輯上將其與其他代碼分開。</span><span class="sxs-lookup"><span data-stu-id="114df-211">Used to associate a name with a group of related types and modules, to logically separate it from other code.</span></span>|
|`new`|[<span data-ttu-id="114df-212">建構函式</span><span class="sxs-lookup"><span data-stu-id="114df-212">Constructors</span></span>](./members/constructors.md)<br /><br />[<span data-ttu-id="114df-213">約束</span><span class="sxs-lookup"><span data-stu-id="114df-213">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-214">用於聲明、定義或調用創建或可以創建物件的建構函式。</span><span class="sxs-lookup"><span data-stu-id="114df-214">Used to declare, define, or invoke a constructor that creates or that can create an object.</span></span><br /><br /><span data-ttu-id="114df-215">也用於泛型參數約束，以指示類型必須具有特定的建構函式。</span><span class="sxs-lookup"><span data-stu-id="114df-215">Also used in generic parameter constraints to indicate that a type must have a certain constructor.</span></span>|
|`not`|[<span data-ttu-id="114df-216">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="114df-216">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)<br /><br />[<span data-ttu-id="114df-217">約束</span><span class="sxs-lookup"><span data-stu-id="114df-217">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-218">實際上不是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="114df-218">Not actually a keyword.</span></span> <span data-ttu-id="114df-219">但是，`not struct`組合用作泛型參數約束。</span><span class="sxs-lookup"><span data-stu-id="114df-219">However, `not struct` in combination is used as a generic parameter constraint.</span></span>|
|`null`|[<span data-ttu-id="114df-220">空值</span><span class="sxs-lookup"><span data-stu-id="114df-220">Null Values</span></span>](./values/null-values.md)<br /><br />[<span data-ttu-id="114df-221">約束</span><span class="sxs-lookup"><span data-stu-id="114df-221">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-222">指示沒有物件。</span><span class="sxs-lookup"><span data-stu-id="114df-222">Indicates the absence of an object.</span></span><br /><br /><span data-ttu-id="114df-223">也用於泛型參數約束。</span><span class="sxs-lookup"><span data-stu-id="114df-223">Also used in generic parameter constraints.</span></span>|
|`of`|[<span data-ttu-id="114df-224">差別聯集</span><span class="sxs-lookup"><span data-stu-id="114df-224">Discriminated Unions</span></span>](discriminated-unions.md)<br /><br />[<span data-ttu-id="114df-225">委派</span><span class="sxs-lookup"><span data-stu-id="114df-225">Delegates</span></span>](delegates.md)<br /><br />[<span data-ttu-id="114df-226">異常類型</span><span class="sxs-lookup"><span data-stu-id="114df-226">Exception Types</span></span>](./exception-handling/exception-types.md)|<span data-ttu-id="114df-227">在區分聯合中用於指示值類別的類型，以及委託和例外聲明。</span><span class="sxs-lookup"><span data-stu-id="114df-227">Used in discriminated unions to indicate the type of categories of values, and in delegate and exception declarations.</span></span>|
|`open`|[<span data-ttu-id="114df-228">匯入宣告：`open` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="114df-228">Import Declarations: The `open` Keyword</span></span>](import-declarations-the-open-keyword.md)|<span data-ttu-id="114df-229">用於使命名空間或模組的內容無限定地可用。</span><span class="sxs-lookup"><span data-stu-id="114df-229">Used to make the contents of a namespace or module available without qualification.</span></span>|
|`or`|[<span data-ttu-id="114df-230">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="114df-230">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)<br /><br />[<span data-ttu-id="114df-231">約束</span><span class="sxs-lookup"><span data-stu-id="114df-231">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-232">與布林條件一起使用，作為布林運算子`or`。</span><span class="sxs-lookup"><span data-stu-id="114df-232">Used with Boolean conditions as a Boolean `or` operator.</span></span> <span data-ttu-id="114df-233">相當於 `||`。</span><span class="sxs-lookup"><span data-stu-id="114df-233">Equivalent to `||`.</span></span><br /><br /><span data-ttu-id="114df-234">也用於成員約束。</span><span class="sxs-lookup"><span data-stu-id="114df-234">Also used in member constraints.</span></span>|
|`override`|[<span data-ttu-id="114df-235">成員</span><span class="sxs-lookup"><span data-stu-id="114df-235">Members</span></span>](./members/index.md)|<span data-ttu-id="114df-236">用於實現不同于基本版本的抽象或虛擬方法的版本。</span><span class="sxs-lookup"><span data-stu-id="114df-236">Used to implement a version of an abstract or virtual method that differs from the base version.</span></span>|
|`private`|[<span data-ttu-id="114df-237">存取控制</span><span class="sxs-lookup"><span data-stu-id="114df-237">Access Control</span></span>](access-control.md)|<span data-ttu-id="114df-238">將成員訪問限制為相同類型或模組的代碼。</span><span class="sxs-lookup"><span data-stu-id="114df-238">Restricts access to a member to code in the same type or module.</span></span>|
|`public`|[<span data-ttu-id="114df-239">存取控制</span><span class="sxs-lookup"><span data-stu-id="114df-239">Access Control</span></span>](access-control.md)|<span data-ttu-id="114df-240">允許從類型外部訪問成員。</span><span class="sxs-lookup"><span data-stu-id="114df-240">Allows access to a member from outside the type.</span></span>|
|`rec`|[<span data-ttu-id="114df-241">函式</span><span class="sxs-lookup"><span data-stu-id="114df-241">Functions</span></span>](./functions/index.md)|<span data-ttu-id="114df-242">用於指示函數是遞迴的。</span><span class="sxs-lookup"><span data-stu-id="114df-242">Used to indicate that a function is recursive.</span></span>|
|`return`|[<span data-ttu-id="114df-243">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="114df-243">Asynchronous Workflows</span></span>](Asynchronous-Workflows.md)<br /><br />[<span data-ttu-id="114df-244">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-244">Computation Expressions</span></span>](computation-expressions.md)|<span data-ttu-id="114df-245">用於指示作為計算運算式的結果提供的值。</span><span class="sxs-lookup"><span data-stu-id="114df-245">Used to indicate a value to provide as the result of a computation expression.</span></span>|
|`return!`|[<span data-ttu-id="114df-246">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-246">Computation Expressions</span></span>](computation-expressions.md)<br /><br />[<span data-ttu-id="114df-247">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="114df-247">Asynchronous Workflows</span></span>](asynchronous-workflows.md)|<span data-ttu-id="114df-248">用於指示計算運算式，計算運算式在計算時提供包含計算運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="114df-248">Used to indicate a computation expression that, when evaluated, provides the result of the containing computation expression.</span></span>|
|`select`|[<span data-ttu-id="114df-249">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="114df-249">Query Expressions</span></span>](query-expressions.md)|<span data-ttu-id="114df-250">用於查詢運算式，用於指定要提取的欄位或列。</span><span class="sxs-lookup"><span data-stu-id="114df-250">Used in query expressions to specify what fields or columns to extract.</span></span> <span data-ttu-id="114df-251">請注意，這是一個上下文關鍵字，這意味著它實際上不是保留詞，它的作用類似于在適當的上下文中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="114df-251">Note that this is a contextual keyword, which means that it is not actually a reserved word and it only acts like a keyword in appropriate context.</span></span>|
|`static`|[<span data-ttu-id="114df-252">成員</span><span class="sxs-lookup"><span data-stu-id="114df-252">Members</span></span>](./members/index.md)|<span data-ttu-id="114df-253">用於指示可以在沒有類型實例的情況下調用的方法或屬性，或類型的所有實例之間共用的值成員。</span><span class="sxs-lookup"><span data-stu-id="114df-253">Used to indicate a method or property that can be called without an instance of a type, or a value member that is shared among all instances of a type.</span></span>|
|`struct`|[<span data-ttu-id="114df-254">結構</span><span class="sxs-lookup"><span data-stu-id="114df-254">Structures</span></span>](structures.md)<br /><br /> [<span data-ttu-id="114df-255">Tuple</span><span class="sxs-lookup"><span data-stu-id="114df-255">Tuples</span></span>](tuples.md)<br/><br/>[<span data-ttu-id="114df-256">約束</span><span class="sxs-lookup"><span data-stu-id="114df-256">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-257">用於聲明結構類型。</span><span class="sxs-lookup"><span data-stu-id="114df-257">Used to declare a structure type.</span></span><br /><br/><span data-ttu-id="114df-258">用於指定結構元組。</span><span class="sxs-lookup"><span data-stu-id="114df-258">Used to specify a struct tuple.</span></span><br/><br /><span data-ttu-id="114df-259">也用於泛型參數約束。</span><span class="sxs-lookup"><span data-stu-id="114df-259">Also used in generic parameter constraints.</span></span><br /><br /><span data-ttu-id="114df-260">用於模組定義中的 OCaml 相容性。</span><span class="sxs-lookup"><span data-stu-id="114df-260">Used for OCaml compatibility in module definitions.</span></span>|
|`then`|[<span data-ttu-id="114df-261">條件運算式：`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="114df-261">Conditional Expressions: `if...then...else`</span></span>](conditional-expressions-if-then-else.md)<br /><br />[<span data-ttu-id="114df-262">建構函式</span><span class="sxs-lookup"><span data-stu-id="114df-262">Constructors</span></span>](./members/constructors.md)|<span data-ttu-id="114df-263">在條件運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="114df-263">Used in conditional expressions.</span></span><br /><br /><span data-ttu-id="114df-264">還用於在物件構造後執行副作用。</span><span class="sxs-lookup"><span data-stu-id="114df-264">Also used to perform side effects after object construction.</span></span>|
|`to`|[<span data-ttu-id="114df-265">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-265">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)|<span data-ttu-id="114df-266">在迴圈`for`中使用以指示範圍。</span><span class="sxs-lookup"><span data-stu-id="114df-266">Used in `for` loops to indicate a range.</span></span>|
|`true`|[<span data-ttu-id="114df-267">基本類型</span><span class="sxs-lookup"><span data-stu-id="114df-267">Primitive Types</span></span>](basic-types.md)|<span data-ttu-id="114df-268">用作布林文本。</span><span class="sxs-lookup"><span data-stu-id="114df-268">Used as a Boolean literal.</span></span>|
|`try`|[<span data-ttu-id="114df-269">例外狀況：try...with 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-269">Exceptions: The try...with Expression</span></span>](./exception-handling/the-try-with-expression.md)<br /><br />[<span data-ttu-id="114df-270">例外狀況：try...finally 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-270">Exceptions: The try...finally Expression</span></span>](./exception-handling/the-try-finally-expression.md)|<span data-ttu-id="114df-271">用於引入可能生成異常的代碼塊。</span><span class="sxs-lookup"><span data-stu-id="114df-271">Used to introduce a block of code that might generate an exception.</span></span> <span data-ttu-id="114df-272">與`with`或`finally`一起使用。</span><span class="sxs-lookup"><span data-stu-id="114df-272">Used together with `with` or `finally`.</span></span>|
|`type`|[<span data-ttu-id="114df-273">F# 類型</span><span class="sxs-lookup"><span data-stu-id="114df-273">F# Types</span></span>](fsharp-types.md)<br /><br />[<span data-ttu-id="114df-274">類別</span><span class="sxs-lookup"><span data-stu-id="114df-274">Classes</span></span>](classes.md)<br /><br />[<span data-ttu-id="114df-275">記錄</span><span class="sxs-lookup"><span data-stu-id="114df-275">Records</span></span>](records.md)<br /><br />[<span data-ttu-id="114df-276">結構</span><span class="sxs-lookup"><span data-stu-id="114df-276">Structures</span></span>](structures.md)<br /><br />[<span data-ttu-id="114df-277">列舉</span><span class="sxs-lookup"><span data-stu-id="114df-277">Enumerations</span></span>](enumerations.md)<br /><br />[<span data-ttu-id="114df-278">差別聯集</span><span class="sxs-lookup"><span data-stu-id="114df-278">Discriminated Unions</span></span>](discriminated-unions.md)<br /><br />[<span data-ttu-id="114df-279">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="114df-279">Type Abbreviations</span></span>](type-abbreviations.md)<br /><br />[<span data-ttu-id="114df-280">度量單位</span><span class="sxs-lookup"><span data-stu-id="114df-280">Units of Measure</span></span>](units-of-measure.md)|<span data-ttu-id="114df-281">用於聲明類、記錄、結構、區分聯合、枚舉類型、度量單位或類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="114df-281">Used to declare a class, record, structure, discriminated union, enumeration type, unit of measure, or type abbreviation.</span></span>|
|`upcast`|[<span data-ttu-id="114df-282">轉型和轉換</span><span class="sxs-lookup"><span data-stu-id="114df-282">Casting and Conversions</span></span>](casting-and-conversions.md)|<span data-ttu-id="114df-283">用於轉換為繼承鏈中較高的類型。</span><span class="sxs-lookup"><span data-stu-id="114df-283">Used to convert to a type that is higher in the inheritance chain.</span></span>|
|`use`|[<span data-ttu-id="114df-284">資源管理：`use` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="114df-284">Resource Management: The `use` Keyword</span></span>](resource-management-the-use-keyword.md)|<span data-ttu-id="114df-285">`let`用於需要調用以釋放資源的值`Dispose`。</span><span class="sxs-lookup"><span data-stu-id="114df-285">Used instead of `let` for values that require `Dispose` to be called to free resources.</span></span>|
|`use!`|[<span data-ttu-id="114df-286">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-286">Computation Expressions</span></span>](computation-expressions.md)<br /><br />[<span data-ttu-id="114df-287">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="114df-287">Asynchronous Workflows</span></span>](asynchronous-workflows.md)|<span data-ttu-id="114df-288">在非同步`let!`工作流和其他計算運算式中用於需要`Dispose`調用以釋放資源的值。</span><span class="sxs-lookup"><span data-stu-id="114df-288">Used instead of `let!` in asynchronous workflows and other computation expressions for values that require `Dispose` to be called to free resources.</span></span>|
|`val`|[<span data-ttu-id="114df-289">明確欄位：`val` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="114df-289">Explicit Fields: The `val` Keyword</span></span>](./members/explicit-fields-the-val-keyword.md)<br /><br />[<span data-ttu-id="114df-290">簽章</span><span class="sxs-lookup"><span data-stu-id="114df-290">Signatures</span></span>](signature-files.md)<br /><br />[<span data-ttu-id="114df-291">成員</span><span class="sxs-lookup"><span data-stu-id="114df-291">Members</span></span>](./members/index.md)|<span data-ttu-id="114df-292">在簽名中用於指示值，或在有限的情況下以型別宣告成員。</span><span class="sxs-lookup"><span data-stu-id="114df-292">Used in a signature to indicate a value, or in a type to declare a member, in limited situations.</span></span>|
|`void`|[<span data-ttu-id="114df-293">基本類型</span><span class="sxs-lookup"><span data-stu-id="114df-293">Primitive Types</span></span>](basic-types.md)|<span data-ttu-id="114df-294">指示 .NET`void`類型。</span><span class="sxs-lookup"><span data-stu-id="114df-294">Indicates the .NET `void` type.</span></span> <span data-ttu-id="114df-295">與其他 .NET 語言交互操作時使用。</span><span class="sxs-lookup"><span data-stu-id="114df-295">Used when interoperating with other .NET languages.</span></span>|
|`when`|[<span data-ttu-id="114df-296">約束</span><span class="sxs-lookup"><span data-stu-id="114df-296">Constraints</span></span>](./generics/constraints.md)|<span data-ttu-id="114df-297">用於模式匹配的布林條件 （*當防護*），並為泛型型別參數引入約束子句。</span><span class="sxs-lookup"><span data-stu-id="114df-297">Used for Boolean conditions (*when guards*) on pattern matches and to introduce a constraint clause for a generic type parameter.</span></span>|
|`while`|[<span data-ttu-id="114df-298">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-298">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)|<span data-ttu-id="114df-299">引入迴圈構造。</span><span class="sxs-lookup"><span data-stu-id="114df-299">Introduces a looping construct.</span></span>|
|`with`|[<span data-ttu-id="114df-300">比對運算式</span><span class="sxs-lookup"><span data-stu-id="114df-300">Match Expressions</span></span>](match-expressions.md)<br /><br />[<span data-ttu-id="114df-301">物件運算式</span><span class="sxs-lookup"><span data-stu-id="114df-301">Object Expressions</span></span>](object-expressions.md)<br /><br />[<span data-ttu-id="114df-302">複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="114df-302">Copy and Update Record Expressions</span></span>](copy-and-update-record-expressions.md)<br /><br />[<span data-ttu-id="114df-303">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="114df-303">Type Extensions</span></span>](type-extensions.md)<br /><br />[<span data-ttu-id="114df-304">例外狀況：`try...with` 運算式</span><span class="sxs-lookup"><span data-stu-id="114df-304">Exceptions: The `try...with` Expression</span></span>](./exception-handling/the-try-with-expression.md)|<span data-ttu-id="114df-305">與模式匹配運算式`match`中的關鍵字一起使用。</span><span class="sxs-lookup"><span data-stu-id="114df-305">Used together with the `match` keyword in pattern matching expressions.</span></span> <span data-ttu-id="114df-306">還用於物件運算式、記錄複製運算式和類型擴展以引入成員定義和引入例外處理常式。</span><span class="sxs-lookup"><span data-stu-id="114df-306">Also used in object expressions, record copying expressions, and type extensions to introduce member definitions, and to introduce exception handlers.</span></span>|
|`yield`|<span data-ttu-id="114df-307">[清單](lists.md)、[陣列](arrays.md)、[序列](sequences.md)</span><span class="sxs-lookup"><span data-stu-id="114df-307">[Lists](lists.md), [Arrays](arrays.md), [Sequences](sequences.md)</span></span>|<span data-ttu-id="114df-308">在清單、陣列或序列運算式中用於生成序列的值。</span><span class="sxs-lookup"><span data-stu-id="114df-308">Used in a list, array, or sequence expression to produce a value for a sequence.</span></span> <span data-ttu-id="114df-309">通常可以省略，因為它在大多數情況下是隱式的。</span><span class="sxs-lookup"><span data-stu-id="114df-309">Typically can be omitted, as it is implicit in most situations.</span></span>|
|`yield!`|[<span data-ttu-id="114df-310">計算運算式</span><span class="sxs-lookup"><span data-stu-id="114df-310">Computation Expressions</span></span>](computation-expressions.md)<br /><br />[<span data-ttu-id="114df-311">非同步工作流程</span><span class="sxs-lookup"><span data-stu-id="114df-311">Asynchronous Workflows</span></span>](asynchronous-workflows.md)|<span data-ttu-id="114df-312">在計算運算式中用於將給定計算運算式的結果追加到包含計算運算式的結果集合中。</span><span class="sxs-lookup"><span data-stu-id="114df-312">Used in a computation expression to append the result of a given computation expression to a collection of results for the containing computation expression.</span></span>|

<span data-ttu-id="114df-313">以下權杖在 F# 中保留，因為它們是 OCaml 語言中的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="114df-313">The following tokens are reserved in F# because they are keywords in the OCaml language:</span></span>

- `asr`
- `land`
- `lor`
- `lsl`
- `lsr`
- `lxor`
- `mod`
- `sig`

<span data-ttu-id="114df-314">如果使用`--mlcompatibility`編譯器選項，則上述關鍵字可用於識別碼。</span><span class="sxs-lookup"><span data-stu-id="114df-314">If you use the `--mlcompatibility` compiler option, the above keywords are available for use as identifiers.</span></span>

<span data-ttu-id="114df-315">以下權杖保留為關鍵字，以供將來擴展 F# 語言：</span><span class="sxs-lookup"><span data-stu-id="114df-315">The following tokens are reserved as keywords for future expansion of the F# language:</span></span>

- `atomic`
- `break`
- `checked`
- `component`
- `const`
- `constraint`
- `constructor`
- `continue`
- `eager`
- `event`
- `external`
- `functor`
- `include`
- `method`
- `mixin`
- `object`
- `parallel`
- `process`
- `protected`
- `pure`
- `sealed`
- `tailcall`
- `trait`
- `virtual`
- `volatile`

## <a name="see-also"></a><span data-ttu-id="114df-316">另請參閱</span><span class="sxs-lookup"><span data-stu-id="114df-316">See also</span></span>

- [<span data-ttu-id="114df-317">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="114df-317">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="114df-318">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="114df-318">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)
- [<span data-ttu-id="114df-319">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="114df-319">Compiler Options</span></span>](compiler-options.md)
