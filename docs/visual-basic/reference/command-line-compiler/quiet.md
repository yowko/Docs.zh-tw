---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005287"
---
# <a name="-quiet"></a><span data-ttu-id="a5d11-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="a5d11-102">-quiet</span></span>

<span data-ttu-id="a5d11-103">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5d11-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="a5d11-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5d11-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="a5d11-105">備註</span><span class="sxs-lookup"><span data-stu-id="a5d11-105">Remarks</span></span>

<span data-ttu-id="a5d11-106">`-quiet` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="a5d11-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="a5d11-107">當編譯器報告語法相關的錯誤或警告時，它也會從原始程式碼輸出這一行。</span><span class="sxs-lookup"><span data-stu-id="a5d11-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="a5d11-108">對於剖析編譯器輸出的應用程式而言，編譯器可能更方便只輸出診斷的文字。</span><span class="sxs-lookup"><span data-stu-id="a5d11-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="a5d11-109">在下列範例中，`Module1` 會在編譯時輸出包含原始程式碼的錯誤，而不 `-quiet`。</span><span class="sxs-lookup"><span data-stu-id="a5d11-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="a5d11-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="a5d11-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="a5d11-111">以 `-quiet` 編譯，編譯器只會輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="a5d11-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="a5d11-112">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="a5d11-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a5d11-113">範例</span><span class="sxs-lookup"><span data-stu-id="a5d11-113">Example</span></span>

<span data-ttu-id="a5d11-114">下列程式碼會編譯 `T2.vb`，而且不會顯示語法相關編譯器診斷的程式碼：</span><span class="sxs-lookup"><span data-stu-id="a5d11-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a5d11-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5d11-115">See also</span></span>

- [<span data-ttu-id="a5d11-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a5d11-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a5d11-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="a5d11-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
