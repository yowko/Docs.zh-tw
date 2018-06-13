---
title: 原始碼程式行、檔案與路徑識別項 (F#)
description: '了解如何使用內建 F # 識別碼的值可讓您存取原始程式碼行號、 目錄和檔案名稱，在程式碼中。'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565213"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="679d8-103">原始碼程式行、檔案與路徑識別項</span><span class="sxs-lookup"><span data-stu-id="679d8-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="679d8-104">識別項`__LINE__`，`__SOURCE_DIRECTORY__`和`__SOURCE_FILE__`是內建可讓您存取您的程式碼的來源行號、 目錄和檔案名稱的值。</span><span class="sxs-lookup"><span data-stu-id="679d8-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="679d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="679d8-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="679d8-106">備註</span><span class="sxs-lookup"><span data-stu-id="679d8-106">Remarks</span></span>
<span data-ttu-id="679d8-107">每個這些值都有類型`string`。</span><span class="sxs-lookup"><span data-stu-id="679d8-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="679d8-108">下表摘要說明原始程式行、 檔案和 F # 中可用的路徑識別項。</span><span class="sxs-lookup"><span data-stu-id="679d8-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="679d8-109">這些識別項不是前置處理器巨集;它們是編譯器可辨識的內建值。</span><span class="sxs-lookup"><span data-stu-id="679d8-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="679d8-110">預先定義的識別項</span><span class="sxs-lookup"><span data-stu-id="679d8-110">Predefined identifier</span></span>|<span data-ttu-id="679d8-111">描述</span><span class="sxs-lookup"><span data-stu-id="679d8-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="679d8-112">判斷值為目前的行號，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="679d8-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="679d8-113">評估目前的完整路徑的來源目錄中，為考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="679d8-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="679d8-114">判斷值為目前的來源檔案名稱和其路徑中，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="679d8-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="679d8-115">如需有關`#line`指示詞，請參閱[編譯器指示詞](compiler-directives.md)。</span><span class="sxs-lookup"><span data-stu-id="679d8-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="679d8-116">範例</span><span class="sxs-lookup"><span data-stu-id="679d8-116">Example</span></span>

<span data-ttu-id="679d8-117">下列程式碼範例示範如何使用這些值。</span><span class="sxs-lookup"><span data-stu-id="679d8-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="679d8-118">輸出：</span><span class="sxs-lookup"><span data-stu-id="679d8-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="679d8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="679d8-119">See Also</span></span>
[<span data-ttu-id="679d8-120">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="679d8-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="679d8-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="679d8-121">F# Language Reference</span></span>](index.md)
