---
title: "程式碼格式化方針 (F#)"
description: "F # 程式語言的可讀性、 美學、 標準化及編譯，了解程式碼縮排格式的指導方針。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3f79717c-f84e-448d-9ce4-90e40a644ba1
ms.openlocfilehash: cc56c67f356b99defd8dc28770f87be1f58443c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="code-formatting-guidelines"></a><span data-ttu-id="2b9a2-104">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="2b9a2-104">Code Formatting Guidelines</span></span>

<span data-ttu-id="2b9a2-105">本主題會摘要 F # 程式碼縮排的指導方針。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-105">This topic summarizes code indentation guidelines for F#.</span></span> <span data-ttu-id="2b9a2-106">因為敏感分行符號和縮排的 F # 語言，不是只可讀性問題、 美觀的問題或若要正確地格式化您的程式碼的程式碼撰寫標準化問題。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-106">Because the F# language is sensitive to line breaks and indentation, it is not just a readability issue, aesthetic issue, or coding standardization issue to format your code correctly.</span></span> <span data-ttu-id="2b9a2-107">您必須正確，才能正確編譯的程式碼的格式。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-107">You must format your code correctly for it to compile correctly.</span></span>


## <a name="general-rules-for-indentation"></a><span data-ttu-id="2b9a2-108">縮排的一般規則</span><span class="sxs-lookup"><span data-stu-id="2b9a2-108">General Rules for Indentation</span></span>
<span data-ttu-id="2b9a2-109">需要縮排時，您必須使用空間，而不是索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-109">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="2b9a2-110">需要至少一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-110">At least one space is required.</span></span> <span data-ttu-id="2b9a2-111">您的組織可以建立以指定要用來縮排; 的空格數目編碼標準通常會發生縮排每個層級的縮排的三或四個空格。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-111">Your organization can create coding standards to specify the number of spaces to use for indentation; three or four spaces of indentation at each level where indentation occurs is typical.</span></span> <span data-ttu-id="2b9a2-112">您可以設定 Visual Studio，以變更的選項，以符合您組織的縮排標準`Options`對話方塊中，可從`Tools`功能表。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-112">You can configure Visual Studio to match your organization's indentation standards by changing the options in the `Options` dialog box, which is available from the `Tools` menu.</span></span> <span data-ttu-id="2b9a2-113">在`Text Editor` 節點，展開  `F#` ，然後按一下  `Tabs`。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-113">In the `Text Editor` node, expand `F#` and then click `Tabs`.</span></span> <span data-ttu-id="2b9a2-114">如需可用之選項的說明，請參閱[選項、 文字編輯器、 所有語言、 索引標籤](https://msdn.microsoft.com/library/7sffa753.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-114">For a description of the available options, see [Options, Text Editor, All Languages, Tabs](https://msdn.microsoft.com/library/7sffa753.aspx).</span></span>

<span data-ttu-id="2b9a2-115">一般情況下，當編譯器剖析您的程式碼，它會保留內部堆疊，指出目前的巢狀層級。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-115">In general, when the compiler parses your code, it maintains an internal stack that indicates the current level of nesting.</span></span> <span data-ttu-id="2b9a2-116">當程式碼就會縮排時，新的層級的巢狀結構會在建立或推送到這個內部堆疊上。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-116">When code is indented, a new level of nesting is created, or pushed onto this internal stack.</span></span> <span data-ttu-id="2b9a2-117">建構結束時，則會彈出層級。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-117">When a construct ends, the level is popped.</span></span> <span data-ttu-id="2b9a2-118">縮排層級的結尾和 pop 內部堆疊，一種方法，但特定語彙基元也會導致層級即可推出，例如`end`關鍵字，或右大括號或括號。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-118">Indentation is one way to signal the end of a level and pop the internal stack, but certain tokens also cause the level to be popped, such as the `end` keyword, or a closing brace or parenthesis.</span></span>

<span data-ttu-id="2b9a2-119">多行的建構，例如的類型定義中的程式碼函式定義`try...with`建構和迴圈建構，必須縮排相對於建構的開頭行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-119">Code in a multiline construct, such as a type definition, function definition, `try...with` construct, and looping constructs, must be indented relative to the opening line of the construct.</span></span> <span data-ttu-id="2b9a2-120">首行縮排相同的建構函式建立後續的程式碼的資料行位置。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-120">The first indented line establishes a column position for subsequent code in the same construct.</span></span> <span data-ttu-id="2b9a2-121">縮排層級稱為*內容*。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-121">The indentation level is called a *context*.</span></span> <span data-ttu-id="2b9a2-122">資料行位置設定的最小的資料行，稱為*越位行*，後續的程式碼行的程式碼是在相同的內容。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-122">The column position sets a minimum column, referred to as an *offside line*, for subsequent lines of code that are in the same context.</span></span> <span data-ttu-id="2b9a2-123">遇到一行程式碼時較少比這個位置上建立資料行縮排，編譯器會假設已結束內容和，您要現在撰寫程式碼在下一個層級，在先前的內容。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-123">When a line of code is encountered that is indented less than this established column position, the compiler assumes that the context has ended and that you are now coding at the next level up, in the previous context.</span></span> <span data-ttu-id="2b9a2-124">詞彙*越位*用來描述的條件，因為它不會縮排到足以觸發建構結尾的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-124">The term *offside* is used to describe the condition in which a line of code triggers the end of a construct because it is not indented far enough.</span></span> <span data-ttu-id="2b9a2-125">換句話說，左邊的越位行程式碼是越位。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-125">In other words, code to the left of an offside line is offside.</span></span> <span data-ttu-id="2b9a2-126">正確縮排程式碼中，您利用越位規則才能描寫建構結尾。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-126">In correctly indented code, you take advantage of the offside rule in order to delineate the end of constructs.</span></span> <span data-ttu-id="2b9a2-127">如果您不當使用縮排，越位狀況會導致編譯器發出警告，或可能會導致您的程式碼不正確解譯。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-127">If you use indentation improperly, an offside condition can cause the compiler to issue a warning or can lead to the incorrect interpretation of your code.</span></span>

<span data-ttu-id="2b9a2-128">越位行決定，如下所示。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-128">Offside lines are determined as follows.</span></span>


- <span data-ttu-id="2b9a2-129">`=`與相關聯的語彙基元`let`導入了位於第一個語彙基元之後的資料行越位行`=`符號。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-129">An `=` token associated with a `let` introduces an offside line at the column of the first token after the `=` sign.</span></span>


- <span data-ttu-id="2b9a2-130">在`if...then...else`運算式、 資料行的位置之後的第一個語彙基元`then`關鍵字或`else`關鍵字導入了越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-130">In an `if...then...else` expression, the column position of the first token after the `then` keyword or the `else` keyword introduces an offside line.</span></span>


- <span data-ttu-id="2b9a2-131">在`try...with`運算式、 後的第一個語彙基元`try`介紹越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-131">In a `try...with` expression, the first token after `try` introduces an offside line.</span></span>


- <span data-ttu-id="2b9a2-132">在`match`運算式、 後的第一個語彙基元`with`和第一個語彙基元之後每個,`->`引入越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-132">In a `match` expression, the first token after `with` and the first token after each `->` introduce offside lines.</span></span>


- <span data-ttu-id="2b9a2-133">之後的第一個語彙基元`with`類型擴充功能引進了越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-133">The first token after `with` in a type extension introduces an offside line.</span></span>


- <span data-ttu-id="2b9a2-134">第一個語彙基元之後的左大括號或括號，或在`begin`關鍵字，導入了越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-134">The first token after an opening brace or parenthesis, or after the `begin` keyword, introduces an offside line.</span></span>


- <span data-ttu-id="2b9a2-135">關鍵字的第一個字元`let`， `if`，和`module`引入越位行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-135">The first character in the keywords `let`, `if`, and `module` introduce offside lines.</span></span>


<span data-ttu-id="2b9a2-136">下列程式碼範例說明的縮排規則。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-136">The following code examples illustrate the indentation rules.</span></span> <span data-ttu-id="2b9a2-137">在這裡，print 陳述式會依賴縮排至與適當的內容產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-137">Here, the print statements rely on indentation to associate them with the appropriate context.</span></span> <span data-ttu-id="2b9a2-138">每次將縮排，取出內容，並返回先前的內容。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-138">Every time the indentation shifts, the context is popped and returns to the previous context.</span></span> <span data-ttu-id="2b9a2-139">因此，空格會列印結尾的每個反覆項目。「 完成 」 ！</span><span class="sxs-lookup"><span data-stu-id="2b9a2-139">Therefore, a space is printed at the end of each iteration; "Done!"</span></span> <span data-ttu-id="2b9a2-140">只列印一次，因為越位縮排會建立不是在迴圈的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-140">is only printed one time because the offside indentation establishes that it is not part of the loop.</span></span> <span data-ttu-id="2b9a2-141">字串 「 最上層內容 」 的列印不是函式的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-141">The printing of the string "Top-level context" is not part of the function.</span></span> <span data-ttu-id="2b9a2-142">因此，它會先列印的靜態初始化期間，會在呼叫函式之前。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-142">Therefore, it is printed first, during the static initialization, before the function is called.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

<span data-ttu-id="2b9a2-143">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-143">The output is as follows.</span></span>

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

<span data-ttu-id="2b9a2-144">當您中斷長行時，行接續必須縮排至封入建構。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-144">When you break long lines, the continuation of the line must be indented farther than the enclosing construct.</span></span> <span data-ttu-id="2b9a2-145">例如，函式引數必須縮排至第一個字元的函式名稱，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-145">For example, function arguments must be indented farther than the first character of the function name, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

<span data-ttu-id="2b9a2-146">下一節中所述，則需要有這些規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-146">There are exceptions to these rules, as described in the next section.</span></span>


## <a name="indentation-in-modules"></a><span data-ttu-id="2b9a2-147">在模組中的縮排</span><span class="sxs-lookup"><span data-stu-id="2b9a2-147">Indentation in Modules</span></span>
<span data-ttu-id="2b9a2-148">在本機的模組中的程式碼必須縮排相對於模組，但最上層的模組中的程式碼不一定要縮排。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-148">Code in a local module must be indented relative to the module, but code in a top-level module does not have to be indented.</span></span> <span data-ttu-id="2b9a2-149">命名空間元素不具有縮排。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-149">Namespace elements do not have to be indented.</span></span>

<span data-ttu-id="2b9a2-150">下列程式碼範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-150">The following code examples illustrate this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

<span data-ttu-id="2b9a2-151">如需詳細資訊，請參閱[模組](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-151">For more information, see [Modules](modules.md).</span></span>


## <a name="exceptions-to-the-basic-indentation-rules"></a><span data-ttu-id="2b9a2-152">基本的縮排規則的例外狀況</span><span class="sxs-lookup"><span data-stu-id="2b9a2-152">Exceptions to the Basic Indentation Rules</span></span>
<span data-ttu-id="2b9a2-153">一般的規則上, 一節中所述是多行建構中的程式碼必須相對於建構的第一行的縮排會縮排和第一個越位行發生時，由決定建構結尾。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-153">The general rule, as described in the previous section, is that code in multiline constructs must be indented relative to the indentation of the first line of the construct, and that the end of the construct is determined by when the first offside line occurs.</span></span> <span data-ttu-id="2b9a2-154">相關內容結束時，某些建構，例如規則的例外狀況`try...with`運算式`if...then...else`運算式，以及使用`and`語法來宣告相互遞迴函式或類型，有多個部分。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-154">An exception to the rule about when contexts end is that some constructs, such as the `try...with` expression, the `if...then...else` expression, and the use of `and` syntax for declaring mutually recursive functions or types, have multiple parts.</span></span> <span data-ttu-id="2b9a2-155">您縮排的更新版本的組件，例如`then`和`else`中`if...then...else`運算式，在相同層級做為權杖啟動運算式，但而不是指出內容結束時，它代表相同的內容中的下一個部分。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-155">You indent the later parts, such as `then` and `else` in an `if...then...else` expression, at the same level as the token that starts the expression, but instead of indicating an end to the context, it represents the next part of the same context.</span></span> <span data-ttu-id="2b9a2-156">因此，`if...then...else`可以撰寫運算式，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-156">Therefore, an `if...then...else` expression can be written as in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

<span data-ttu-id="2b9a2-157">越位規則的例外狀況只會套用到`then`和`else`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-157">The exception to the offside rule applies only to the `then` and `else` keywords.</span></span> <span data-ttu-id="2b9a2-158">因此，雖然這並非要縮排錯誤`then`和`else`進一步，失敗的縮排中的程式碼行`then`區塊會產生警告。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-158">Therefore, although it is not an error to indent the `then` and `else` further, failing to indent the lines of code in a `then` block produces a warning.</span></span> <span data-ttu-id="2b9a2-159">下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-159">This is illustrated in the following lines of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

<span data-ttu-id="2b9a2-160">中的程式碼`else`適用於區塊中，有額外的特殊規則。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-160">For code in an `else` block, an additional special rule applies.</span></span> <span data-ttu-id="2b9a2-161">上述範例中的警告，就會發生在程式碼中`then`區塊中，不是在中的程式碼`else`區塊。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-161">The warning in the previous example occurs only on the code in the `then` block, not on the code in the `else` block.</span></span> <span data-ttu-id="2b9a2-162">這可讓您撰寫程式碼，而不未強制其餘的函式，這可能是在程式碼會檢查開頭函式的各種狀況`else`區塊，縮排。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-162">This allows you to write code that checks for various conditions at the beginning of a function without forcing the rest of the code for the function, which might be in an `else` block, to be indented.</span></span> <span data-ttu-id="2b9a2-163">因此，您可以撰寫下列不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-163">Thus, you can write the following without producing a warning.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

<span data-ttu-id="2b9a2-164">另一個例外狀況時一條線不會縮排就前一行是中置運算子，例如，結束內容的規則`+`和`|>`。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-164">Another exception to the rule that contexts end when a line is not indented as far as a previous line is for infix operators, such as `+` and `|>`.</span></span> <span data-ttu-id="2b9a2-165">允許中置運算子為開頭的行開始`(1 + oplength)`正常的位置，而不觸發內容結束之前的資料行其中`oplength`會運算子構成的字元數。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-165">Lines that start with infix operators are permitted to begin `(1 + oplength)` columns before the normal position without triggering an end to the context, where `oplength` is the number of characters that make up the operator.</span></span> <span data-ttu-id="2b9a2-166">這會導致第一個語彙基元來對齊上下行運算子後面。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-166">This causes the first token after the operator to align with the previous line.</span></span>

<span data-ttu-id="2b9a2-167">例如，在下列程式碼，`+`符號可以是小於前一行的縮排的兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-167">For example, in the following code, the `+` symbol is permitted to be indented two columns less than the previous line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

<span data-ttu-id="2b9a2-168">雖然的巢狀層級更高版本時，通常會增加縮排，有數個建構在其中編譯器可讓您重設為較低的資料行位置的縮排。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-168">Although indentation usually increases as the level of nesting becomes higher, there are several constructs in which the compiler allows you to reset the indentation to a lower column position.</span></span>

<span data-ttu-id="2b9a2-169">允許的資料行位置重設的建構如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b9a2-169">The constructs that permit a reset of column position are as follows:</span></span>


- <span data-ttu-id="2b9a2-170">匿名函式的主體。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-170">Bodies of anonymous functions.</span></span> <span data-ttu-id="2b9a2-171">下列程式碼中，列印的運算式會從資料行位置更遠比左側`fun`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-171">In the following code, the print expression starts at a column position that is farther to the left than the `fun` keyword.</span></span> <span data-ttu-id="2b9a2-172">不過，在列不能在左邊開始的上一個縮排層級的資料行 (也就是左邊`L`中`List`)。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-172">However, the line must not start at a column to the left of the start of the previous indentation level (that is, to the left of the `L` in `List`).</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- <span data-ttu-id="2b9a2-173">建構括以括號或`begin`和`end`中`then`或`else`區塊`if...then...else`運算式，提供縮排是不小於的資料行位置`if`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-173">Constructs enclosed by parentheses or by `begin` and `end` in a `then` or `else` block of an `if...then...else` expression, provided the indentation is no less than the column position of the `if` keyword.</span></span> <span data-ttu-id="2b9a2-174">這個例外狀況允許編碼樣式所在左括號或`begin`結尾的後一條線使用`then`或`else`。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-174">This exception allows for a coding style in which an opening parenthesis or `begin` is used at the end of a line after `then` or `else`.</span></span>


- <span data-ttu-id="2b9a2-175">主體的模組、 類別、 介面和結構，以分隔`begin...end`， `{...}`， `class...end`，或`interface...end`。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-175">Bodies of modules, classes, interfaces, and structures delimited by `begin...end`, `{...}`, `class...end`, or `interface...end`.</span></span> <span data-ttu-id="2b9a2-176">這可讓您在其中開啟關鍵字型別定義的型別名稱的同一行不能強制執行是開啟關鍵字至縮排的整個主體樣式。</span><span class="sxs-lookup"><span data-stu-id="2b9a2-176">This allows for a style in which the opening keyword of a type definition can be on the same line as the type name without forcing the whole body to be indented farther than the opening keyword.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a><span data-ttu-id="2b9a2-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b9a2-177">See Also</span></span>
[<span data-ttu-id="2b9a2-178">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="2b9a2-178">F# Language Reference</span></span>](index.md)
