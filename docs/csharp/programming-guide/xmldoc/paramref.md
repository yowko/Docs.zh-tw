---
title: '<paramref>-C # 程式設計指南'
description: 瞭解 XML <paramref> 標記。 此標記可讓您指定程式碼中的單字為參數。
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381836"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="ab915-104">\<paramref>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="ab915-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab915-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab915-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="ab915-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab915-106">Parameters</span></span>

- `name`

  <span data-ttu-id="ab915-107">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="ab915-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="ab915-108">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="ab915-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="ab915-109">備註</span><span class="sxs-lookup"><span data-stu-id="ab915-109">Remarks</span></span>

<span data-ttu-id="ab915-110">`<paramref>`標記可讓您指定程式碼批註中的單字，例如在 `<summary>` 或區塊中 `<remarks>` 參考參數。</span><span class="sxs-lookup"><span data-stu-id="ab915-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="ab915-111">若要以某種不同方式 (例如，粗體或斜體字型) 格式化這個字組，您可以處理 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab915-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="ab915-112">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="ab915-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ab915-113">範例</span><span class="sxs-lookup"><span data-stu-id="ab915-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="ab915-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab915-114">See also</span></span>

- [<span data-ttu-id="ab915-115">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ab915-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ab915-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="ab915-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
