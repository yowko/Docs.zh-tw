---
title: <list> - C#程式設計指南
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789745"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="78547-102">\<清單 > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="78547-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="78547-103">語法</span><span class="sxs-lookup"><span data-stu-id="78547-103">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="78547-104">參數</span><span class="sxs-lookup"><span data-stu-id="78547-104">Parameters</span></span>

- `term`

  <span data-ttu-id="78547-105">要定義的詞彙，可定義於 `description` 中。</span><span class="sxs-lookup"><span data-stu-id="78547-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="78547-106">項目符號或編號清單中的項目或者 `term` 的定義。</span><span class="sxs-lookup"><span data-stu-id="78547-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="78547-107">備註</span><span class="sxs-lookup"><span data-stu-id="78547-107">Remarks</span></span>

<span data-ttu-id="78547-108">\<listheader> 區塊用來定義資料表或定義清單的標題資料列。</span><span class="sxs-lookup"><span data-stu-id="78547-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="78547-109">定義資料表時，您只需要提供標題中詞彙的項目。</span><span class="sxs-lookup"><span data-stu-id="78547-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="78547-110">清單中的每個項目都是使用 \<item> 區塊所指定。</span><span class="sxs-lookup"><span data-stu-id="78547-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="78547-111">建立定義清單時，您需要同時指定 `term` 和 `description`。</span><span class="sxs-lookup"><span data-stu-id="78547-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="78547-112">不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。</span><span class="sxs-lookup"><span data-stu-id="78547-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="78547-113">清單或資料表可以有所需的多個 \<item> 區塊。</span><span class="sxs-lookup"><span data-stu-id="78547-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="78547-114">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="78547-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="78547-115">範例</span><span class="sxs-lookup"><span data-stu-id="78547-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="78547-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="78547-116">See also</span></span>

- [<span data-ttu-id="78547-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="78547-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="78547-118">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="78547-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
