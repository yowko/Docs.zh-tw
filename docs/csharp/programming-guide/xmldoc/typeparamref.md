---
title: '<typeparamref>-C # 程式設計指南'
description: 瞭解 XML <typeparamref> 標記。 此標記可讓檔檔案的取用者以某種不同的方式來格式化單字，例如以斜體表示。
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380718"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="6055e-104">\<typeparamref>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="6055e-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6055e-105">語法</span><span class="sxs-lookup"><span data-stu-id="6055e-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="6055e-106">參數</span><span class="sxs-lookup"><span data-stu-id="6055e-106">Parameters</span></span>

- `name`

  <span data-ttu-id="6055e-107">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6055e-107">The name of the type parameter.</span></span> <span data-ttu-id="6055e-108">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="6055e-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="6055e-109">備註</span><span class="sxs-lookup"><span data-stu-id="6055e-109">Remarks</span></span>

<span data-ttu-id="6055e-110">如需泛型型別和方法中型別參數的詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6055e-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="6055e-111">使用這個標記，讓文件檔案的取用者以某種明顯方式格式化單字，例如斜體。</span><span class="sxs-lookup"><span data-stu-id="6055e-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="6055e-112">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="6055e-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="6055e-113">範例</span><span class="sxs-lookup"><span data-stu-id="6055e-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="6055e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6055e-114">See also</span></span>

- [<span data-ttu-id="6055e-115">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="6055e-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6055e-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="6055e-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
