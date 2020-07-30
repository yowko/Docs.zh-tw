---
title: '<list> -C # 程式設計指南'
description: 瞭解 XML <list> 的相片或視訊。 此標記用來建立資料表和定義、以點符或編號的清單，方法是使用 ' item ' 區塊。
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381862"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="c7454-105">\<list>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="c7454-105">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7454-106">語法</span><span class="sxs-lookup"><span data-stu-id="c7454-106">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="c7454-107">參數</span><span class="sxs-lookup"><span data-stu-id="c7454-107">Parameters</span></span>

- `term`

  <span data-ttu-id="c7454-108">要定義的詞彙，可定義於 `description` 中。</span><span class="sxs-lookup"><span data-stu-id="c7454-108">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="c7454-109">項目符號或編號清單中的項目或者 `term` 的定義。</span><span class="sxs-lookup"><span data-stu-id="c7454-109">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="c7454-110">備註</span><span class="sxs-lookup"><span data-stu-id="c7454-110">Remarks</span></span>

<span data-ttu-id="c7454-111">`<listheader>`區塊是用來定義資料表或定義清單的標題資料列。</span><span class="sxs-lookup"><span data-stu-id="c7454-111">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="c7454-112">定義資料表時，您只需要提供標題中詞彙的項目。</span><span class="sxs-lookup"><span data-stu-id="c7454-112">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="c7454-113">清單中的每個專案都是以 `<item>` 區塊來指定。</span><span class="sxs-lookup"><span data-stu-id="c7454-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="c7454-114">建立定義清單時，您需要同時指定 `term` 和 `description`。</span><span class="sxs-lookup"><span data-stu-id="c7454-114">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="c7454-115">不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。</span><span class="sxs-lookup"><span data-stu-id="c7454-115">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="c7454-116">清單或資料表可以視需要擁有多個 `<item>` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c7454-116">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="c7454-117">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="c7454-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c7454-118">範例</span><span class="sxs-lookup"><span data-stu-id="c7454-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="c7454-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7454-119">See also</span></span>

- [<span data-ttu-id="c7454-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="c7454-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c7454-121">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="c7454-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
