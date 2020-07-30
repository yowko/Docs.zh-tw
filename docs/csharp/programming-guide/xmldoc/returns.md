---
title: '<returns> -C # 程式設計指南'
description: 瞭解 XML <returns> 的相片或視訊。 此標記會用於方法宣告的批註中，以描述傳回值。
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381394"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="1020e-105">\<returns>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="1020e-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1020e-106">語法</span><span class="sxs-lookup"><span data-stu-id="1020e-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="1020e-107">參數</span><span class="sxs-lookup"><span data-stu-id="1020e-107">Parameters</span></span>

- `description`

  <span data-ttu-id="1020e-108">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="1020e-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="1020e-109">備註</span><span class="sxs-lookup"><span data-stu-id="1020e-109">Remarks</span></span>

<span data-ttu-id="1020e-110">`<returns>`標記應該用於方法宣告的批註中，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="1020e-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="1020e-111">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="1020e-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1020e-112">範例</span><span class="sxs-lookup"><span data-stu-id="1020e-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="1020e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1020e-113">See also</span></span>

- [<span data-ttu-id="1020e-114">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1020e-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1020e-115">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="1020e-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
