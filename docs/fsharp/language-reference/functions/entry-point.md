---
title: 進入點 (F#)
description: '了解如何設定為 編譯為可執行檔，正式開始執行 F # 程式的進入點。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 42e5fe7f85285f990ef92e9791ed5bdfacb85059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="entry-point"></a><span data-ttu-id="a0765-103">進入點</span><span class="sxs-lookup"><span data-stu-id="a0765-103">Entry Point</span></span>

<span data-ttu-id="a0765-104">本主題描述您用來設定 F # 程式的進入點方法。</span><span class="sxs-lookup"><span data-stu-id="a0765-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="a0765-105">語法</span><span class="sxs-lookup"><span data-stu-id="a0765-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="a0765-106">備註</span><span class="sxs-lookup"><span data-stu-id="a0765-106">Remarks</span></span>
<span data-ttu-id="a0765-107">在先前的語法，*讓函式繫結*是在函式定義`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="a0765-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="a0765-108">會編譯為可執行檔是正式開始執行程式進入點。</span><span class="sxs-lookup"><span data-stu-id="a0765-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="a0765-109">您套用指定的 F # 應用程式的進入點`EntryPoint`屬性的程式`main`函式。</span><span class="sxs-lookup"><span data-stu-id="a0765-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="a0765-110">此函式 (使用建立`let`繫結) 必須是最後一個編譯檔案中的最後一個函式。</span><span class="sxs-lookup"><span data-stu-id="a0765-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="a0765-111">最後一個已編譯的檔案是專案中的最後一個檔案或傳遞至命令列的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="a0765-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="a0765-112">進入點函式具有類型`string array -> int`。</span><span class="sxs-lookup"><span data-stu-id="a0765-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="a0765-113">在命令列上所提供的引數會傳遞至`main`函式的字串陣列中。</span><span class="sxs-lookup"><span data-stu-id="a0765-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="a0765-114">陣列的第一個項目是第一個引數。可執行檔的名稱不會包含在陣列中，因為它是其他語言中。</span><span class="sxs-lookup"><span data-stu-id="a0765-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="a0765-115">處理序結束碼為使用的傳回值。</span><span class="sxs-lookup"><span data-stu-id="a0765-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="a0765-116">零通常會表示成功。非零值表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="a0765-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="a0765-117">沒有任何特定的意義，則為非零的傳回碼; 的慣例傳回碼的意義是特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0765-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="a0765-118">下列範例將說明簡單`main`函式。</span><span class="sxs-lookup"><span data-stu-id="a0765-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="a0765-119">使用命令列執行此程式碼時`EntryPoint.exe 1 2 3`，輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="a0765-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="a0765-120">隱含的進入點</span><span class="sxs-lookup"><span data-stu-id="a0765-120">Implicit Entry Point</span></span>
<span data-ttu-id="a0765-121">當程式沒有任何**EntryPoint**屬性會明確指出 進入點，最後一個檔案中編譯的最上層繫結會用做為進入點。</span><span class="sxs-lookup"><span data-stu-id="a0765-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="a0765-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0765-122">See Also</span></span>
[<span data-ttu-id="a0765-123">函式</span><span class="sxs-lookup"><span data-stu-id="a0765-123">Functions</span></span>](index.md)

[<span data-ttu-id="a0765-124">let 繫結</span><span class="sxs-lookup"><span data-stu-id="a0765-124">let Bindings</span></span>](let-bindings.md)
