---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716708"
---
# <a name="-netcf"></a><span data-ttu-id="c5d97-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="c5d97-102">-netcf</span></span>

<span data-ttu-id="c5d97-103">設定編譯器以 .NET Compact Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="c5d97-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5d97-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5d97-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="c5d97-105">備註</span><span class="sxs-lookup"><span data-stu-id="c5d97-105">Remarks</span></span>

<span data-ttu-id="c5d97-106">`-netcf`選項會導致 Visual Basic 編譯器以 .NET Compact Framework 為目標，而不是完整 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="c5d97-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="c5d97-107">只在完整 .NET Framework 中顯示的語言功能已停用。</span><span class="sxs-lookup"><span data-stu-id="c5d97-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="c5d97-108">`-netcf`選項是設計來搭配[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)使用。</span><span class="sxs-lookup"><span data-stu-id="c5d97-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="c5d97-109">所停`-netcf`用的語言功能，與以`-sdkpath`為目標的檔案中不存在相同的語言功能。</span><span class="sxs-lookup"><span data-stu-id="c5d97-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="c5d97-110">此`-netcf`選項無法在 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="c5d97-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="c5d97-111">當`-netcf`載入 Visual Basic 裝置專案時，就會設定此選項。</span><span class="sxs-lookup"><span data-stu-id="c5d97-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="c5d97-112">`-netcf`選項會變更下列語言功能：</span><span class="sxs-lookup"><span data-stu-id="c5d97-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="c5d97-113">[End \<關鍵字> 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字（終止程式的執行）已停用。</span><span class="sxs-lookup"><span data-stu-id="c5d97-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="c5d97-114">下列程式會`-netcf`編譯並執行，但在編譯時期會失敗`-netcf`。</span><span class="sxs-lookup"><span data-stu-id="c5d97-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="c5d97-115">所有形式的晚期繫結都會停用。</span><span class="sxs-lookup"><span data-stu-id="c5d97-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="c5d97-116">遇到可識別的晚期繫結案例時，就會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5d97-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="c5d97-117">下列程式會`-netcf`編譯並執行，但在編譯時期會失敗`-netcf`。</span><span class="sxs-lookup"><span data-stu-id="c5d97-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="c5d97-118">[Auto](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)和[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞已停用。</span><span class="sxs-lookup"><span data-stu-id="c5d97-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="c5d97-119">[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)的語法也會修改為`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。</span><span class="sxs-lookup"><span data-stu-id="c5d97-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="c5d97-120">下列程式碼會顯示編譯`-netcf`時的效果。</span><span class="sxs-lookup"><span data-stu-id="c5d97-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="c5d97-121">使用從 Visual Basic 移除的 Visual Basic 6.0 關鍵字會在使用時`-netcf`產生不同的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5d97-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="c5d97-122">這會影響下列關鍵字的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="c5d97-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="c5d97-123">範例</span><span class="sxs-lookup"><span data-stu-id="c5d97-123">Example</span></span>

<span data-ttu-id="c5d97-124">下列程式碼會`Myfile.vb`使用 .NET Compact Framework 進行編譯，其方式是在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到 Mscorlib.dll 和 Microsoft 的版本。</span><span class="sxs-lookup"><span data-stu-id="c5d97-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="c5d97-125">一般來說，您會使用最新版本的 .NET Compact Framework。</span><span class="sxs-lookup"><span data-stu-id="c5d97-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="c5d97-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5d97-126">See also</span></span>

- [<span data-ttu-id="c5d97-127">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="c5d97-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c5d97-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="c5d97-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c5d97-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="c5d97-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
