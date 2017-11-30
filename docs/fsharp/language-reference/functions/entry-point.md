---
title: "進入點 (F#)"
description: "了解如何設定為 編譯為可執行檔，正式開始執行 F # 程式的進入點。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="34dc4-104">進入點</span><span class="sxs-lookup"><span data-stu-id="34dc4-104">Entry Point</span></span>

<span data-ttu-id="34dc4-105">本主題描述您用來設定 F # 程式的進入點方法。</span><span class="sxs-lookup"><span data-stu-id="34dc4-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="34dc4-106">語法</span><span class="sxs-lookup"><span data-stu-id="34dc4-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="34dc4-107">備註</span><span class="sxs-lookup"><span data-stu-id="34dc4-107">Remarks</span></span>
<span data-ttu-id="34dc4-108">在先前的語法，*讓函式繫結*是在函式定義`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="34dc4-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="34dc4-109">會編譯為可執行檔是正式開始執行程式進入點。</span><span class="sxs-lookup"><span data-stu-id="34dc4-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="34dc4-110">您套用指定的 F # 應用程式的進入點`EntryPoint`屬性的程式`main`函式。</span><span class="sxs-lookup"><span data-stu-id="34dc4-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="34dc4-111">此函式 (使用建立`let`繫結) 必須是最後一個編譯檔案中的最後一個函式。</span><span class="sxs-lookup"><span data-stu-id="34dc4-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="34dc4-112">最後一個已編譯的檔案是專案中的最後一個檔案或傳遞至命令列的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="34dc4-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="34dc4-113">進入點函式具有類型`string array -> int`。</span><span class="sxs-lookup"><span data-stu-id="34dc4-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="34dc4-114">在命令列上所提供的引數會傳遞至`main`函式的字串陣列中。</span><span class="sxs-lookup"><span data-stu-id="34dc4-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="34dc4-115">陣列的第一個項目是第一個引數。可執行檔的名稱不會包含在陣列中，因為它是其他語言中。</span><span class="sxs-lookup"><span data-stu-id="34dc4-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="34dc4-116">處理序結束碼為使用的傳回值。</span><span class="sxs-lookup"><span data-stu-id="34dc4-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="34dc4-117">零通常會表示成功。非零值表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="34dc4-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="34dc4-118">沒有任何特定的意義，則為非零的傳回碼; 的慣例傳回碼的意義是特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="34dc4-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="34dc4-119">下列範例將說明簡單`main`函式。</span><span class="sxs-lookup"><span data-stu-id="34dc4-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="34dc4-120">使用命令列執行此程式碼時`EntryPoint.exe 1 2 3`，輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="34dc4-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="34dc4-121">隱含的進入點</span><span class="sxs-lookup"><span data-stu-id="34dc4-121">Implicit Entry Point</span></span>
<span data-ttu-id="34dc4-122">當程式沒有任何**EntryPoint**屬性會明確指出 進入點，最後一個檔案中編譯的最上層繫結會用做為進入點。</span><span class="sxs-lookup"><span data-stu-id="34dc4-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="34dc4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34dc4-123">See Also</span></span>
[<span data-ttu-id="34dc4-124">函式</span><span class="sxs-lookup"><span data-stu-id="34dc4-124">Functions</span></span>](index.md)

[<span data-ttu-id="34dc4-125">let 繫結</span><span class="sxs-lookup"><span data-stu-id="34dc4-125">let Bindings</span></span>](let-bindings.md)
