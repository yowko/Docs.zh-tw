---
title: <remarks> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793378"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="9478c-102">\<注釋>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="9478c-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9478c-103">語法</span><span class="sxs-lookup"><span data-stu-id="9478c-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="9478c-104">參數</span><span class="sxs-lookup"><span data-stu-id="9478c-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="9478c-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="9478c-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="9478c-106">備註</span><span class="sxs-lookup"><span data-stu-id="9478c-106">Remarks</span></span>

<span data-ttu-id="9478c-107">注釋\<>標記用於添加有關類型的資訊，以[\<摘要>](./summary.md)指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="9478c-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="9478c-108">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="9478c-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="9478c-109">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="9478c-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9478c-110">範例</span><span class="sxs-lookup"><span data-stu-id="9478c-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="9478c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9478c-111">See also</span></span>

- [<span data-ttu-id="9478c-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9478c-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9478c-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="9478c-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
