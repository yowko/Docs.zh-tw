---
title: '<para> -C # 程式設計指南'
description: 瞭解 XML <para> 的相片或視訊。 此標記可讓您將結構新增至另一個標記中的文字，例如 <summary>, <remarks>或 <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 146078bcb556b4085724ddcdac561ea868ab0481
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381849"
---
# <a name="para-c-programming-guide"></a><span data-ttu-id="75938-108">\<para>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="75938-108">\<para> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="75938-109">語法</span><span class="sxs-lookup"><span data-stu-id="75938-109">Syntax</span></span>

```xml
<para>content</para>
```

## <a name="parameters"></a><span data-ttu-id="75938-110">參數</span><span class="sxs-lookup"><span data-stu-id="75938-110">Parameters</span></span>

- `content`

  <span data-ttu-id="75938-111">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="75938-111">The text of the paragraph.</span></span>

## <a name="remarks"></a><span data-ttu-id="75938-112">備註</span><span class="sxs-lookup"><span data-stu-id="75938-112">Remarks</span></span>

<span data-ttu-id="75938-113">`<para>`標記用於標記內（例如 [\<summary>](./summary.md) 、 [\<remarks>](./remarks.md) 或 [\<returns>](./returns.md) ），並可讓您將結構新增至文字。</span><span class="sxs-lookup"><span data-stu-id="75938-113">The `<para>` tag is for use inside a tag, such as [\<summary>](./summary.md), [\<remarks>](./remarks.md), or [\<returns>](./returns.md), and lets you add structure to the text.</span></span>

<span data-ttu-id="75938-114">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="75938-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="75938-115">範例</span><span class="sxs-lookup"><span data-stu-id="75938-115">Example</span></span>

<span data-ttu-id="75938-116">如需使用的範例，請參閱 [\<summary>](./summary.md) `<para>` 。</span><span class="sxs-lookup"><span data-stu-id="75938-116">See [\<summary>](./summary.md) for an example of using `<para>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="75938-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75938-117">See also</span></span>

- [<span data-ttu-id="75938-118">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="75938-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="75938-119">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="75938-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
