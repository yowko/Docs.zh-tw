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
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400522"
---
# <a name="-quiet"></a><span data-ttu-id="02014-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="02014-102">-quiet</span></span>

<span data-ttu-id="02014-103">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="02014-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="02014-104">語法</span><span class="sxs-lookup"><span data-stu-id="02014-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="02014-105">備註</span><span class="sxs-lookup"><span data-stu-id="02014-105">Remarks</span></span>

<span data-ttu-id="02014-106">`-quiet` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="02014-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="02014-107">當編譯器報告語法相關的錯誤或警告時，它也會從原始程式碼輸出這一行。</span><span class="sxs-lookup"><span data-stu-id="02014-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="02014-108">對於剖析編譯器輸出的應用程式而言，編譯器可能更方便只輸出診斷的文字。</span><span class="sxs-lookup"><span data-stu-id="02014-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="02014-109">在下列範例中， `Module1` 會在不使用編譯時輸出包含原始程式碼的錯誤 `-quiet` 。</span><span class="sxs-lookup"><span data-stu-id="02014-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="02014-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="02014-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="02014-111">以編譯時 `-quiet` ，編譯器只會輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="02014-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="02014-112">此 `-quiet` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="02014-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="02014-113">範例</span><span class="sxs-lookup"><span data-stu-id="02014-113">Example</span></span>

<span data-ttu-id="02014-114">下列 `T2.vb` 程式碼會編譯，且不會顯示語法相關編譯器診斷的程式碼：</span><span class="sxs-lookup"><span data-stu-id="02014-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="02014-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02014-115">See also</span></span>

- [<span data-ttu-id="02014-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="02014-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="02014-117">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="02014-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
