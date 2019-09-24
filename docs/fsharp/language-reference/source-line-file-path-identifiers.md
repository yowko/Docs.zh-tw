---
title: 原始碼程式行、檔案與路徑識別項
description: 瞭解如何使用內F#建的識別碼值，讓您存取程式碼中的原始程式列號、目錄和檔案名。
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216754"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="da11d-103">原始碼程式行、檔案與路徑識別項</span><span class="sxs-lookup"><span data-stu-id="da11d-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="da11d-104">識別碼`__LINE__` `__SOURCE_DIRECTORY__`和是內建值，可讓您存取程式碼中的原始程式列號、目錄和檔案名。`__SOURCE_FILE__`</span><span class="sxs-lookup"><span data-stu-id="da11d-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="da11d-105">語法</span><span class="sxs-lookup"><span data-stu-id="da11d-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="da11d-106">備註</span><span class="sxs-lookup"><span data-stu-id="da11d-106">Remarks</span></span>

<span data-ttu-id="da11d-107">這些值的每一個都`string`具有類型。</span><span class="sxs-lookup"><span data-stu-id="da11d-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="da11d-108">下表摘要說明中F#可用的原始程式列、檔案和路徑識別碼。</span><span class="sxs-lookup"><span data-stu-id="da11d-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="da11d-109">這些識別碼不是預處理器宏;這些是編譯器可辨識的內建值。</span><span class="sxs-lookup"><span data-stu-id="da11d-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="da11d-110">預先定義的識別碼</span><span class="sxs-lookup"><span data-stu-id="da11d-110">Predefined identifier</span></span>|<span data-ttu-id="da11d-111">描述</span><span class="sxs-lookup"><span data-stu-id="da11d-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="da11d-112">評估為目前的行號，並`#line`考慮指示詞。</span><span class="sxs-lookup"><span data-stu-id="da11d-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="da11d-113">評估為來原始目錄的目前完整路徑，並考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="da11d-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="da11d-114">評估為目前的來原始檔案名，不含其路徑，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="da11d-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="da11d-115">如需指示詞的`#line`詳細資訊，請參閱[編譯器](compiler-directives.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="da11d-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="da11d-116">範例</span><span class="sxs-lookup"><span data-stu-id="da11d-116">Example</span></span>

<span data-ttu-id="da11d-117">下列程式碼範例示範如何使用這些值。</span><span class="sxs-lookup"><span data-stu-id="da11d-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="da11d-118">輸出：</span><span class="sxs-lookup"><span data-stu-id="da11d-118">Output:</span></span>

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="da11d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da11d-119">See also</span></span>

- [<span data-ttu-id="da11d-120">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="da11d-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="da11d-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="da11d-121">F# Language Reference</span></span>](index.md)
