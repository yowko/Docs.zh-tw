---
title: '<returns> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287229"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="5bf9e-102">\<returns>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="5bf9e-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="5bf9e-103">語法</span><span class="sxs-lookup"><span data-stu-id="5bf9e-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="5bf9e-104">參數</span><span class="sxs-lookup"><span data-stu-id="5bf9e-104">Parameters</span></span>

- `description`

  <span data-ttu-id="5bf9e-105">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="5bf9e-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bf9e-106">備註</span><span class="sxs-lookup"><span data-stu-id="5bf9e-106">Remarks</span></span>

<span data-ttu-id="5bf9e-107">`<returns>`標記應該用於方法宣告的批註中，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="5bf9e-107">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="5bf9e-108">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="5bf9e-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="5bf9e-109">範例</span><span class="sxs-lookup"><span data-stu-id="5bf9e-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="5bf9e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bf9e-110">See also</span></span>

- [<span data-ttu-id="5bf9e-111">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="5bf9e-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="5bf9e-112">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="5bf9e-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
