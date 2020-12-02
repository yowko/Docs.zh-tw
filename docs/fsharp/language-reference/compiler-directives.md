---
title: 編譯器指示詞
description: '瞭解 F # 語言預處理器指示詞、條件式編譯指示詞、行指示詞和編譯器指示詞。'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: ff106339478c3413dc6458b12f12e1d3f9cd1fe5
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438179"
---
# <a name="compiler-directives"></a><span data-ttu-id="d067b-103">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-103">Compiler Directives</span></span>

<span data-ttu-id="d067b-104">本主題描述處理器指示詞和編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-104">This topic describes processor directives and compiler directives.</span></span>

## <a name="preprocessor-directives"></a><span data-ttu-id="d067b-105">前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-105">Preprocessor Directives</span></span>

<span data-ttu-id="d067b-106">前置處理器指示詞的字首會加上 # 符號，且自身會出現在一行中。</span><span class="sxs-lookup"><span data-stu-id="d067b-106">A preprocessor directive is prefixed with the # symbol and appears on a line by itself.</span></span> <span data-ttu-id="d067b-107">它是由前置處理器解譯，會在編譯器本身之前執行。</span><span class="sxs-lookup"><span data-stu-id="d067b-107">It is interpreted by the preprocessor, which runs before the compiler itself.</span></span>

<span data-ttu-id="d067b-108">下表列出 F# 中可用的前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-108">The following table lists the preprocessor directives that are available in F#.</span></span>

|<span data-ttu-id="d067b-109">指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-109">Directive</span></span>|<span data-ttu-id="d067b-110">描述</span><span class="sxs-lookup"><span data-stu-id="d067b-110">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="d067b-111">`#if`*符號*</span><span class="sxs-lookup"><span data-stu-id="d067b-111">`#if` *symbol*</span></span>|<span data-ttu-id="d067b-112">支援條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="d067b-112">Supports conditional compilation.</span></span> <span data-ttu-id="d067b-113">如果已定義符號，則 `#if` 會包含後面區段 *symbol* 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d067b-113">Code in the section after the `#if` is included if the *symbol* is defined.</span></span> <span data-ttu-id="d067b-114">符號也可以使用否定 `!` 。</span><span class="sxs-lookup"><span data-stu-id="d067b-114">The symbol can also be negated with `!`.</span></span>|
|`#else`|<span data-ttu-id="d067b-115">支援條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="d067b-115">Supports conditional compilation.</span></span> <span data-ttu-id="d067b-116">若未定義與先前的 `#if` 搭配使用的符號，則標記要包含的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="d067b-116">Marks a section of code to include if the symbol used with the previous `#if` is not defined.</span></span>|
|`#endif`|<span data-ttu-id="d067b-117">支援條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="d067b-117">Supports conditional compilation.</span></span> <span data-ttu-id="d067b-118">標示程式碼的條件式區段結尾。</span><span class="sxs-lookup"><span data-stu-id="d067b-118">Marks the end of a conditional section of code.</span></span>|
|<span data-ttu-id="d067b-119">`#`行 *int*、</span><span class="sxs-lookup"><span data-stu-id="d067b-119">`#`[line] *int*,</span></span><br/><span data-ttu-id="d067b-120">`#`行 *int* *字串*，</span><span class="sxs-lookup"><span data-stu-id="d067b-120">`#`[line] *int* *string*,</span></span><br/><span data-ttu-id="d067b-121">`#`行 *int* *逐字字串*</span><span class="sxs-lookup"><span data-stu-id="d067b-121">`#`[line] *int* *verbatim-string*</span></span>|<span data-ttu-id="d067b-122">表示原始的原始程式碼行和檔案名稱 (適用於偵錯)。</span><span class="sxs-lookup"><span data-stu-id="d067b-122">Indicates the original source code line and file name, for debugging.</span></span> <span data-ttu-id="d067b-123">這項功能提供用於產生 F# 原始程式碼的工具。</span><span class="sxs-lookup"><span data-stu-id="d067b-123">This feature is provided for tools that generate F# source code.</span></span>|
|<span data-ttu-id="d067b-124">`#nowarn`*warningcode*</span><span class="sxs-lookup"><span data-stu-id="d067b-124">`#nowarn` *warningcode*</span></span>|<span data-ttu-id="d067b-125">停用編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="d067b-125">Disables a compiler warning or warnings.</span></span> <span data-ttu-id="d067b-126">若要停用警告，請從編譯器輸出中找出其號碼並包含在引號中。</span><span class="sxs-lookup"><span data-stu-id="d067b-126">To disable a warning, find its number from the compiler output and include it in quotation marks.</span></span> <span data-ttu-id="d067b-127">略過 "FS" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-127">Omit the "FS" prefix.</span></span> <span data-ttu-id="d067b-128">若要停用同一行的多個警告號碼，請以引號括住每個號碼，並以一個空格分隔每個字串。</span><span class="sxs-lookup"><span data-stu-id="d067b-128">To disable multiple warning numbers on the same line, include each number in quotation marks, and separate each string by a space.</span></span> <span data-ttu-id="d067b-129">例如：</span><span class="sxs-lookup"><span data-stu-id="d067b-129">For example:</span></span>

`#nowarn "9" "40"`

<span data-ttu-id="d067b-130">停用警告的效果會套用到整個檔案，包括指示詞前面的檔案部分。 |</span><span class="sxs-lookup"><span data-stu-id="d067b-130">The effect of disabling a warning applies to the entire file, including portions of the file that precede the directive.|</span></span>

## <a name="conditional-compilation-directives"></a><span data-ttu-id="d067b-131">條件式編譯指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-131">Conditional Compilation Directives</span></span>

<span data-ttu-id="d067b-132">其中一個指示詞停用的程式碼在 Visual Studio Code 編輯器中會呈現暗灰色。</span><span class="sxs-lookup"><span data-stu-id="d067b-132">Code that is deactivated by one of these directives appears dimmed in the Visual Studio Code Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="d067b-133">條件式編譯指示詞的行為與其在其他語言的行為不同。</span><span class="sxs-lookup"><span data-stu-id="d067b-133">The behavior of the conditional compilation directives is not the same as it is in other languages.</span></span> <span data-ttu-id="d067b-134">例如，您無法使用包含符號的布林運算式，且 `true` 和 `false` 沒有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="d067b-134">For example, you cannot use Boolean expressions involving symbols, and `true` and `false` have no special meaning.</span></span> <span data-ttu-id="d067b-135">在 `if` 指示詞中使用的符號必須透過命令列定義，或在專案設定中定義；沒有任何 `define` 前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-135">Symbols that you use in the `if` directive must be defined by the command line or in the project settings; there is no `define` preprocessor directive.</span></span>

<span data-ttu-id="d067b-136">下列程式碼說明如何使用 `#if`、`#else` 和 `#endif` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-136">The following code illustrates the use of the `#if`, `#else`, and `#endif` directives.</span></span> <span data-ttu-id="d067b-137">在此範例中，程式碼包含兩個版本的 `function1` 定義。</span><span class="sxs-lookup"><span data-stu-id="d067b-137">In this example, the code contains two versions of the definition of `function1`.</span></span> <span data-ttu-id="d067b-138">當 `VERSION1` 使用 [-define 編譯器選項](./compiler-options.md)定義時，會啟動指示詞與指示詞之間的程式碼 `#if` `#else` 。</span><span class="sxs-lookup"><span data-stu-id="d067b-138">When `VERSION1` is defined by using the [-define compiler option](./compiler-options.md), the code between the `#if` directive and the `#else` directive is activated.</span></span> <span data-ttu-id="d067b-139">否則會啟動 `#else` 與 `#endif` 之間的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d067b-139">Otherwise, the code between `#else` and `#endif` is activated.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

<span data-ttu-id="d067b-140">F# 中沒有 `#define` 前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-140">There is no `#define` preprocessor directive in F#.</span></span> <span data-ttu-id="d067b-141">您必須使用編譯器選項或專案設定來定義 `#if` 指示詞所使用的符號。</span><span class="sxs-lookup"><span data-stu-id="d067b-141">You must use the compiler option or project settings to define the symbols used by the `#if` directive.</span></span>

<span data-ttu-id="d067b-142">條件式編譯指示詞可以巢狀化。</span><span class="sxs-lookup"><span data-stu-id="d067b-142">Conditional compilation directives can be nested.</span></span> <span data-ttu-id="d067b-143">縮排對於前置處理器指示詞而言不重要。</span><span class="sxs-lookup"><span data-stu-id="d067b-143">Indentation is not significant for preprocessor directives.</span></span>

<span data-ttu-id="d067b-144">您也可以使用來對符號進行否定 `!` 。</span><span class="sxs-lookup"><span data-stu-id="d067b-144">You can also negate a symbol with `!`.</span></span> <span data-ttu-id="d067b-145">在此範例中，只有在 _不_ 進行偵錯工具時，才會有字串的值：</span><span class="sxs-lookup"><span data-stu-id="d067b-145">In this example, a string's value is something only when _not_ debugging:</span></span>

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a><span data-ttu-id="d067b-146">行指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-146">Line Directives</span></span>

<span data-ttu-id="d067b-147">建置時，編譯器會參考發生的每個錯誤所在的行號，以報告 F# 程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d067b-147">When building, the compiler reports errors in F# code by referencing line numbers on which each error occurs.</span></span> <span data-ttu-id="d067b-148">這些行號從 1 開始，從檔案的第一行起算。</span><span class="sxs-lookup"><span data-stu-id="d067b-148">These line numbers start at 1 for the first line in a file.</span></span> <span data-ttu-id="d067b-149">不過，如果您正在從另一個工具產生 F# 原始程式碼，產生的程式碼中的行號通常不重要，因為產生的 F# 程式碼中的錯誤很可能來自其他來源。</span><span class="sxs-lookup"><span data-stu-id="d067b-149">However, if you are generating F# source code from another tool, the line numbers in the generated code are generally not of interest, because the errors in the generated F# code most likely arise from another source.</span></span> <span data-ttu-id="d067b-150">`#line` 指示詞為工具的作者提供一種方式，即產生 F# 原始程式碼，將有關原始行號和來源檔案的相關資訊傳遞給產生的 F# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d067b-150">The `#line` directive provides a way for authors of tools that generate F# source code to pass information about the original line numbers and source files to the generated F# code.</span></span>

<span data-ttu-id="d067b-151">使用 `#line` 指示詞時，檔案名稱必須括在引號內。</span><span class="sxs-lookup"><span data-stu-id="d067b-151">When you use the `#line` directive, file names must be enclosed in quotation marks.</span></span> <span data-ttu-id="d067b-152">除非逐字語彙基元 (`@`) 會出現在字串前面，否則必須逸出反斜線字元 (使用兩個反斜線字元而非一個)，才能在路徑中使用它們。</span><span class="sxs-lookup"><span data-stu-id="d067b-152">Unless the verbatim token (`@`) appears in front of the string, you must escape backslash characters by using two backslash characters instead of one in order to use them in the path.</span></span> <span data-ttu-id="d067b-153">下面是有效的行語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d067b-153">The following are valid line tokens.</span></span> <span data-ttu-id="d067b-154">在這些範例中，假設透過工具執行原始檔案 `Script1` 時，會自動產生 F# 程式碼檔案，並會在 `Script1` 檔的第 25 行，從某些語彙基元中產生這些指示詞位置處的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d067b-154">In these examples, assume that the original file `Script1` results in an automatically generated F# code file when it is run through a tool, and that the code at the location of these directives is generated from some tokens at line 25 in file `Script1`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

<span data-ttu-id="d067b-155">這些語彙基元指出在這個位置產生的 F# 程式碼，是衍生自 `Script1` 的 `25` 行或附近的某些建構。</span><span class="sxs-lookup"><span data-stu-id="d067b-155">These tokens indicate that the F# code generated at this location is derived from some constructs at or near line `25` in `Script1`.</span></span>

## <a name="compiler-directives"></a><span data-ttu-id="d067b-156">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-156">Compiler Directives</span></span>

<span data-ttu-id="d067b-157">編譯器指示詞類似前置處理器指示詞，因為它們會加上 # 符號前置詞，但不是由前置處理器解譯，而是留給編譯器解譯及處理。</span><span class="sxs-lookup"><span data-stu-id="d067b-157">Compiler directives resemble preprocessor directives, because they are prefixed with a # sign, but instead of being interpreted by the preprocessor, they are left for the compiler to interpret and act on.</span></span>

<span data-ttu-id="d067b-158">下表列出可在 F# 中使用的編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="d067b-158">The following table lists the compiler directive that is available in F#.</span></span>

|<span data-ttu-id="d067b-159">指示詞</span><span class="sxs-lookup"><span data-stu-id="d067b-159">Directive</span></span>|<span data-ttu-id="d067b-160">描述</span><span class="sxs-lookup"><span data-stu-id="d067b-160">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="d067b-161">`#light` [on "&#124;" off "]</span><span class="sxs-lookup"><span data-stu-id="d067b-161">`#light` ["on"&#124;"off"]</span></span>|<span data-ttu-id="d067b-162">啟用或停用輕量型語法，與其他 ML 版本相容。</span><span class="sxs-lookup"><span data-stu-id="d067b-162">Enables or disables lightweight syntax, for compatibility with other versions of ML.</span></span> <span data-ttu-id="d067b-163">根據預設，會啟用輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="d067b-163">By default, lightweight syntax is enabled.</span></span> <span data-ttu-id="d067b-164">一律會啟用詳細語法。</span><span class="sxs-lookup"><span data-stu-id="d067b-164">Verbose syntax is always enabled.</span></span> <span data-ttu-id="d067b-165">因此，您可以使用輕量型語法和詳細語法。</span><span class="sxs-lookup"><span data-stu-id="d067b-165">Therefore, you can use both lightweight syntax and verbose syntax.</span></span> <span data-ttu-id="d067b-166">指示詞 `#light` 本身就相當於 `#light "on"`。</span><span class="sxs-lookup"><span data-stu-id="d067b-166">The directive `#light` by itself is equivalent to `#light "on"`.</span></span> <span data-ttu-id="d067b-167">如果您指定 `#light "off"`，您必須針對所有語言建構使用詳細語法。</span><span class="sxs-lookup"><span data-stu-id="d067b-167">If you specify `#light "off"`, you must use verbose syntax for all language constructs.</span></span> <span data-ttu-id="d067b-168">會假設您使用輕量型語法，在文件中顯示 F# 語法。</span><span class="sxs-lookup"><span data-stu-id="d067b-168">Syntax in the documentation for F# is presented with the assumption that you are using lightweight syntax.</span></span> <span data-ttu-id="d067b-169">如需詳細資訊，請參閱 [詳細資訊語法](verbose-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="d067b-169">For more information, see [Verbose Syntax](verbose-syntax.md).</span></span>|

<span data-ttu-id="d067b-170">如 ( # A0) 指示詞的解譯器，請參閱 [使用 F # 的互動式程式設計](../tools/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d067b-170">For interpreter (fsi.exe) directives, see [Interactive Programming with F#](../tools/fsharp-interactive/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d067b-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d067b-171">See also</span></span>

- [<span data-ttu-id="d067b-172">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="d067b-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d067b-173">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d067b-173">Compiler Options</span></span>](compiler-options.md)
