---
title: 原始碼程式行、檔案與路徑識別項 (F#)
description: '了解如何使用內建 F # 識別項值可讓您存取原始程式碼行號、 目錄和檔案名稱，在您的程式碼。'
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865123"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="bca27-103">原始碼程式行、檔案與路徑識別項</span><span class="sxs-lookup"><span data-stu-id="bca27-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="bca27-104">識別項`__LINE__`，`__SOURCE_DIRECTORY__`和`__SOURCE_FILE__`內建值可讓您存取您的程式碼的來源行號、 目錄和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="bca27-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="bca27-105">語法</span><span class="sxs-lookup"><span data-stu-id="bca27-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="bca27-106">備註</span><span class="sxs-lookup"><span data-stu-id="bca27-106">Remarks</span></span>

<span data-ttu-id="bca27-107">每個這些值都有型別`string`。</span><span class="sxs-lookup"><span data-stu-id="bca27-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="bca27-108">下表摘要說明原始程式行、 檔案和可在 F # 中的路徑識別項。</span><span class="sxs-lookup"><span data-stu-id="bca27-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="bca27-109">這些識別項不是前置處理器巨集;它們是編譯器可辨識的內建值。</span><span class="sxs-lookup"><span data-stu-id="bca27-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="bca27-110">預先定義的識別項</span><span class="sxs-lookup"><span data-stu-id="bca27-110">Predefined identifier</span></span>|<span data-ttu-id="bca27-111">描述</span><span class="sxs-lookup"><span data-stu-id="bca27-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="bca27-112">評估為目前的行號，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="bca27-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="bca27-113">評估為目前的完整路徑的來源目錄中，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="bca27-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="bca27-114">評估為目前的來源檔案名稱和其路徑中，考慮`#line`指示詞。</span><span class="sxs-lookup"><span data-stu-id="bca27-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="bca27-115">如需詳細資訊`#line`指示詞，請參閱[編譯器指示詞](compiler-directives.md)。</span><span class="sxs-lookup"><span data-stu-id="bca27-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="bca27-116">範例</span><span class="sxs-lookup"><span data-stu-id="bca27-116">Example</span></span>

<span data-ttu-id="bca27-117">下列程式碼範例示範如何使用這些值。</span><span class="sxs-lookup"><span data-stu-id="bca27-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="bca27-118">輸出：</span><span class="sxs-lookup"><span data-stu-id="bca27-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="bca27-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca27-119">See also</span></span>

- [<span data-ttu-id="bca27-120">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="bca27-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="bca27-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="bca27-121">F# Language Reference</span></span>](index.md)
