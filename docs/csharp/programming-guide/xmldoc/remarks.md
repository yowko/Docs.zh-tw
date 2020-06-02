---
title: '<remarks> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287281"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="79b5a-102">\<remarks>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="79b5a-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="79b5a-103">語法</span><span class="sxs-lookup"><span data-stu-id="79b5a-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="79b5a-104">參數</span><span class="sxs-lookup"><span data-stu-id="79b5a-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="79b5a-105">成員的描述。</span><span class="sxs-lookup"><span data-stu-id="79b5a-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="79b5a-106">備註</span><span class="sxs-lookup"><span data-stu-id="79b5a-106">Remarks</span></span>

<span data-ttu-id="79b5a-107">`<remarks>`標記是用來加入類型的相關資訊，並補充以指定的資訊 [\<summary>](./summary.md) 。</span><span class="sxs-lookup"><span data-stu-id="79b5a-107">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="79b5a-108">這項資訊會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="79b5a-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="79b5a-109">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="79b5a-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="79b5a-110">範例</span><span class="sxs-lookup"><span data-stu-id="79b5a-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="79b5a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b5a-111">See also</span></span>

- [<span data-ttu-id="79b5a-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="79b5a-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="79b5a-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="79b5a-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
