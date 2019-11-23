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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005456"
---
# <a name="-netcf"></a><span data-ttu-id="1edcd-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="1edcd-102">-netcf</span></span>

<span data-ttu-id="1edcd-103">設定編譯器以 .NET Compact Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="1edcd-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="1edcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="1edcd-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="1edcd-105">備註</span><span class="sxs-lookup"><span data-stu-id="1edcd-105">Remarks</span></span>

<span data-ttu-id="1edcd-106">`-netcf` 選項會使 Visual Basic 編譯器以 .NET Compact Framework 而不是完整 .NET Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="1edcd-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="1edcd-107">只在完整 .NET Framework 中顯示的語言功能已停用。</span><span class="sxs-lookup"><span data-stu-id="1edcd-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="1edcd-108">`-netcf` 選項是設計來搭配[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)使用。</span><span class="sxs-lookup"><span data-stu-id="1edcd-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="1edcd-109">`-netcf` 停用的語言功能，與 `-sdkpath`的目標檔案中不存在相同的語言功能。</span><span class="sxs-lookup"><span data-stu-id="1edcd-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="1edcd-110">Visual Studio 開發環境中無法使用 [`-netcf`] 選項;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="1edcd-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="1edcd-111">[`-netcf`] 選項會在載入 Visual Basic 裝置專案時設定。</span><span class="sxs-lookup"><span data-stu-id="1edcd-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="1edcd-112">`-netcf` 選項會變更下列語言功能：</span><span class="sxs-lookup"><span data-stu-id="1edcd-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="1edcd-113">[End \<關鍵字 > 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字（終止程式的執行）已停用。</span><span class="sxs-lookup"><span data-stu-id="1edcd-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="1edcd-114">下列程式會編譯並執行而不 `-netcf`，但在編譯時期會發生 `-netcf`。</span><span class="sxs-lookup"><span data-stu-id="1edcd-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="1edcd-115">所有形式的晚期繫結都會停用。</span><span class="sxs-lookup"><span data-stu-id="1edcd-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="1edcd-116">遇到可識別的晚期繫結案例時，就會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="1edcd-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="1edcd-117">下列程式會編譯並執行而不 `-netcf`，但在編譯時期會發生 `-netcf`。</span><span class="sxs-lookup"><span data-stu-id="1edcd-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="1edcd-118">[Auto](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)和[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞已停用。</span><span class="sxs-lookup"><span data-stu-id="1edcd-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="1edcd-119">[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)語句的語法也會修改為 `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。</span><span class="sxs-lookup"><span data-stu-id="1edcd-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="1edcd-120">下列程式碼顯示在編譯時 `-netcf` 的效果。</span><span class="sxs-lookup"><span data-stu-id="1edcd-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="1edcd-121">使用從 Visual Basic 移除的 Visual Basic 6.0 關鍵字會在使用 `-netcf` 時產生不同的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1edcd-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="1edcd-122">這會影響下列關鍵字的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="1edcd-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="1edcd-123">範例</span><span class="sxs-lookup"><span data-stu-id="1edcd-123">Example</span></span>

<span data-ttu-id="1edcd-124">下列程式碼會使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 mscorlib.dll 和 default.aspx 版本，以 .NET Compact Framework 編譯 `Myfile.vb`。</span><span class="sxs-lookup"><span data-stu-id="1edcd-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="1edcd-125">一般來說，您會使用最新版本的 .NET Compact Framework。</span><span class="sxs-lookup"><span data-stu-id="1edcd-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="1edcd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1edcd-126">See also</span></span>

- [<span data-ttu-id="1edcd-127">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="1edcd-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1edcd-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="1edcd-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="1edcd-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="1edcd-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
