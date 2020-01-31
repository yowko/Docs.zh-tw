---
title: <returns> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789716"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="89c3a-102">\<傳回 > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="89c3a-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="89c3a-103">語法</span><span class="sxs-lookup"><span data-stu-id="89c3a-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="89c3a-104">參數</span><span class="sxs-lookup"><span data-stu-id="89c3a-104">Parameters</span></span>

- `description`

  <span data-ttu-id="89c3a-105">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="89c3a-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="89c3a-106">備註</span><span class="sxs-lookup"><span data-stu-id="89c3a-106">Remarks</span></span>

<span data-ttu-id="89c3a-107">\<returns> 標記應該用於方法宣告的註解中，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="89c3a-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="89c3a-108">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="89c3a-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="89c3a-109">範例</span><span class="sxs-lookup"><span data-stu-id="89c3a-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="89c3a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="89c3a-110">See also</span></span>

- [<span data-ttu-id="89c3a-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="89c3a-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="89c3a-112">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="89c3a-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
