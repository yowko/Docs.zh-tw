---
title: 原始碼程式行、檔案與路徑識別項
description: 了解如何使用內建的F#可讓您存取來源的識別碼值行編號、 目錄和檔案名稱，在您的程式碼。
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663618"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="edfc4-103">原始碼程式行、檔案與路徑識別項</span><span class="sxs-lookup"><span data-stu-id="edfc4-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="edfc4-104">識別項`__LINE__`，`__SOURCE_DIRECTORY__`和`__SOURCE_FILE__`內建值可讓您存取您的程式碼的來源行號、 目錄和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="edfc4-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="edfc4-105">語法</span><span class="sxs-lookup"><span data-stu-id="edfc4-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="edfc4-106">備註</span><span class="sxs-lookup"><span data-stu-id="edfc4-106">Remarks</span></span>

<span data-ttu-id="edfc4-107">每個這些值都有型別`string`。</span><span class="sxs-lookup"><span data-stu-id="edfc4-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="edfc4-108">下表摘要說明中所提供的來源行、 檔案和路徑識別碼F#。</span><span class="sxs-lookup"><span data-stu-id="edfc4-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="edfc4-109">這些識別項不是前置處理器巨集;它們是編譯器可辨識的內建值。</span><span class="sxs-lookup"><span data-stu-id="edfc4-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="edfc4-110">預先定義的識別項</span><span class="sxs-lookup"><span data-stu-id="edfc4-110">Predefined identifier</span></span>|<span data-ttu-id="edfc4-111">描述</span><span class="sxs-lookup"><span data-stu-id="edfc4-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="edfc4-112">評估為目前的行號，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="edfc4-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="edfc4-113">評估為目前的完整路徑的來源目錄中，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="edfc4-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="edfc4-114">評估為目前的來源檔案名稱和其路徑中，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="edfc4-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|

<span data-ttu-id="edfc4-115">如需詳細資訊`#line`指示詞，請參閱[編譯器指示詞](compiler-directives.md)。</span><span class="sxs-lookup"><span data-stu-id="edfc4-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="edfc4-116">範例</span><span class="sxs-lookup"><span data-stu-id="edfc4-116">Example</span></span>

<span data-ttu-id="edfc4-117">下列程式碼範例示範如何使用這些值。</span><span class="sxs-lookup"><span data-stu-id="edfc4-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="edfc4-118">輸出：</span><span class="sxs-lookup"><span data-stu-id="edfc4-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="edfc4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edfc4-119">See also</span></span>

- [<span data-ttu-id="edfc4-120">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="edfc4-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="edfc4-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="edfc4-121">F# Language Reference</span></span>](index.md)
