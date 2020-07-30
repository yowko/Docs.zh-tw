---
title: '<example> -C # 程式設計指南'
description: 瞭解 XML <example> 的相片或視訊。 此標記可讓您指定如何使用方法或其他程式庫成員的範例。
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381524"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="a5d5f-105">\<example>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="a5d5f-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5d5f-106">語法</span><span class="sxs-lookup"><span data-stu-id="a5d5f-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="a5d5f-107">參數</span><span class="sxs-lookup"><span data-stu-id="a5d5f-107">Parameters</span></span>

- `description`

  <span data-ttu-id="a5d5f-108">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="a5d5f-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5d5f-109">備註</span><span class="sxs-lookup"><span data-stu-id="a5d5f-109">Remarks</span></span>

<span data-ttu-id="a5d5f-110">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="a5d5f-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="a5d5f-111">這通常牽涉到使用 [\<code>](./code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="a5d5f-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="a5d5f-112">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="a5d5f-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a5d5f-113">範例</span><span class="sxs-lookup"><span data-stu-id="a5d5f-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="a5d5f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5d5f-114">See also</span></span>

- [<span data-ttu-id="a5d5f-115">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a5d5f-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5d5f-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="a5d5f-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
