---
title: 進入點
description: 瞭解如何將進入點設定為編譯為F#可執行檔的程式, 其中會正式開始執行。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630529"
---
# <a name="entry-point"></a><span data-ttu-id="93b63-103">進入點</span><span class="sxs-lookup"><span data-stu-id="93b63-103">Entry Point</span></span>

<span data-ttu-id="93b63-104">本主題說明用來設定F#程式進入點的方法。</span><span class="sxs-lookup"><span data-stu-id="93b63-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="93b63-105">語法</span><span class="sxs-lookup"><span data-stu-id="93b63-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="93b63-106">備註</span><span class="sxs-lookup"><span data-stu-id="93b63-106">Remarks</span></span>

<span data-ttu-id="93b63-107">在先前的語法中, *let 函數*系結是系結中`let`函式的定義。</span><span class="sxs-lookup"><span data-stu-id="93b63-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="93b63-108">編譯為可執行檔之程式的進入點是執行正式開始的位置。</span><span class="sxs-lookup"><span data-stu-id="93b63-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="93b63-109">您可以藉由F# `EntryPoint`將屬性套用至程式的`main`函式, 來指定應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="93b63-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="93b63-110">這個函式 (使用`let`系結所建立) 必須是上次編譯檔案中的最後一個函式。</span><span class="sxs-lookup"><span data-stu-id="93b63-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="93b63-111">上次編譯的檔案是專案中的最後一個檔案, 或傳遞至命令列的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="93b63-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="93b63-112">進入點函式具有類型`string array -> int`。</span><span class="sxs-lookup"><span data-stu-id="93b63-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="93b63-113">在命令列上提供的引數會傳遞至`main`字串陣列中的函式。</span><span class="sxs-lookup"><span data-stu-id="93b63-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="93b63-114">陣列的第一個元素是第一個引數;可執行檔的名稱不會包含在陣列中, 因為它是在某些其他語言中。</span><span class="sxs-lookup"><span data-stu-id="93b63-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="93b63-115">傳回值會當做進程的結束代碼使用。</span><span class="sxs-lookup"><span data-stu-id="93b63-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="93b63-116">零通常表示成功;非零值表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="93b63-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="93b63-117">非零傳回碼的特定意義沒有任何慣例;傳回碼的意義是應用程式特有的。</span><span class="sxs-lookup"><span data-stu-id="93b63-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="93b63-118">下列範例說明簡單`main`的函式。</span><span class="sxs-lookup"><span data-stu-id="93b63-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="93b63-119">當使用命令列`EntryPoint.exe 1 2 3`來執行此程式碼時, 輸出會如下所示。</span><span class="sxs-lookup"><span data-stu-id="93b63-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="93b63-120">隱含進入點</span><span class="sxs-lookup"><span data-stu-id="93b63-120">Implicit Entry Point</span></span>

<span data-ttu-id="93b63-121">當程式沒有明確指出進入點的**EntryPoint**屬性時, 最後一個要編譯的檔案中的最上層系結會當做進入點使用。</span><span class="sxs-lookup"><span data-stu-id="93b63-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="93b63-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93b63-122">See also</span></span>

- [<span data-ttu-id="93b63-123">函式</span><span class="sxs-lookup"><span data-stu-id="93b63-123">Functions</span></span>](index.md)
- [<span data-ttu-id="93b63-124">let 繫結</span><span class="sxs-lookup"><span data-stu-id="93b63-124">let Bindings</span></span>](let-bindings.md)
