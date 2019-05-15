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
ms.openlocfilehash: b64c55b73a9c835ded0d7c81ff36329b8d6a8bc9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586538"
---
# <a name="-netcf"></a><span data-ttu-id="93ec0-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="93ec0-102">-netcf</span></span>

<span data-ttu-id="93ec0-103">設定要以 [!INCLUDE[Compact](~/includes/compact-md.md)] 為目標的編譯器。</span><span class="sxs-lookup"><span data-stu-id="93ec0-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>

## <a name="syntax"></a><span data-ttu-id="93ec0-104">語法</span><span class="sxs-lookup"><span data-stu-id="93ec0-104">Syntax</span></span>

```
-netcf
```

## <a name="remarks"></a><span data-ttu-id="93ec0-105">備註</span><span class="sxs-lookup"><span data-stu-id="93ec0-105">Remarks</span></span>

<span data-ttu-id="93ec0-106">`-netcf`選項可讓目標 Visual Basic 編譯器[!INCLUDE[Compact](~/includes/compact-md.md)]而不是完整的.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="93ec0-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full .NET Framework.</span></span> <span data-ttu-id="93ec0-107">是完整的.NET Framework 中的語言功能已停用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="93ec0-108">`-netcf`選項設計來搭配[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)。</span><span class="sxs-lookup"><span data-stu-id="93ec0-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="93ec0-109">停用的語言功能`-netcf`都是相同的語言功能不存在於目標檔案`-sdkpath`。</span><span class="sxs-lookup"><span data-stu-id="93ec0-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="93ec0-110">`-netcf`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="93ec0-111">`-netcf` Visual Basic 裝置專案載入時，設定選項。</span><span class="sxs-lookup"><span data-stu-id="93ec0-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="93ec0-112">`-netcf`選項會變更下列語言功能：</span><span class="sxs-lookup"><span data-stu-id="93ec0-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="93ec0-113">[結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字，結束執行程式，已停用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="93ec0-114">下列程式會編譯並執行時不會`-netcf`會在編譯階段失敗，但`-netcf`。</span><span class="sxs-lookup"><span data-stu-id="93ec0-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="93ec0-115">晚期繫結時，在所有表單中，已停用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="93ec0-116">遇到已辨識的晚期繫結情節時，會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="93ec0-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="93ec0-117">下列程式會編譯並執行時不會`-netcf`會在編譯階段失敗，但`-netcf`。</span><span class="sxs-lookup"><span data-stu-id="93ec0-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="93ec0-118">[自動](../../../visual-basic/language-reference/modifiers/auto.md)， [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)，並[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞會停用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="93ec0-119">語法[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)陳述式也會修改成`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。</span><span class="sxs-lookup"><span data-stu-id="93ec0-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="93ec0-120">下列程式碼顯示的效果`-netcf`在編譯時。</span><span class="sxs-lookup"><span data-stu-id="93ec0-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="93ec0-121">使用 Visual Basic 6.0 已移除從 Visual Basic 的關鍵字會產生不同的錯誤時`-netcf`用。</span><span class="sxs-lookup"><span data-stu-id="93ec0-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="93ec0-122">這會影響下列關鍵字的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93ec0-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="93ec0-123">範例</span><span class="sxs-lookup"><span data-stu-id="93ec0-123">Example</span></span>

<span data-ttu-id="93ec0-124">下列程式碼會編譯`Myfile.vb`具有[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 mscorlib.dll 和 Microsoft.VisualBasic.dll 的新版的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="93ec0-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="93ec0-125">一般而言，您會使用最新版本的[!INCLUDE[Compact](~/includes/compact-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="93ec0-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="93ec0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93ec0-126">See also</span></span>

- [<span data-ttu-id="93ec0-127">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="93ec0-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="93ec0-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="93ec0-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="93ec0-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="93ec0-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
