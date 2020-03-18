---
title: <typeparamref>- C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789664"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="367d4-102">\<類型參數>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="367d4-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="367d4-103">語法</span><span class="sxs-lookup"><span data-stu-id="367d4-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="367d4-104">參數</span><span class="sxs-lookup"><span data-stu-id="367d4-104">Parameters</span></span>

- `name`

  <span data-ttu-id="367d4-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="367d4-105">The name of the type parameter.</span></span> <span data-ttu-id="367d4-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="367d4-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="367d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="367d4-107">Remarks</span></span>

<span data-ttu-id="367d4-108">如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="367d4-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="367d4-109">使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。</span><span class="sxs-lookup"><span data-stu-id="367d4-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="367d4-110">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="367d4-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="367d4-111">範例</span><span class="sxs-lookup"><span data-stu-id="367d4-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="367d4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="367d4-112">See also</span></span>

- [<span data-ttu-id="367d4-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="367d4-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="367d4-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="367d4-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
