---
title: '<remarks> -C # 程式設計指南'
description: 瞭解 XML <remarks> 的相片或視訊。 此標記用來新增類型的相關資訊，並補充以下列方式指定的資訊： <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381498"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="ffaa6-106">\<remarks>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="ffaa6-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ffaa6-107">語法</span><span class="sxs-lookup"><span data-stu-id="ffaa6-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="ffaa6-108">參數</span><span class="sxs-lookup"><span data-stu-id="ffaa6-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="ffaa6-109">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="ffaa6-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffaa6-110">備註</span><span class="sxs-lookup"><span data-stu-id="ffaa6-110">Remarks</span></span>

<span data-ttu-id="ffaa6-111">`<remarks>`標記是用來加入類型的相關資訊，並補充以指定的資訊 [\<summary>](./summary.md) 。</span><span class="sxs-lookup"><span data-stu-id="ffaa6-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="ffaa6-112">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="ffaa6-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="ffaa6-113">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="ffaa6-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ffaa6-114">範例</span><span class="sxs-lookup"><span data-stu-id="ffaa6-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="ffaa6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffaa6-115">See also</span></span>

- [<span data-ttu-id="ffaa6-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ffaa6-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ffaa6-117">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="ffaa6-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
