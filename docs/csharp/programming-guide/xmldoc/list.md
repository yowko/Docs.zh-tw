---
title: '&lt;list&gt; - C# 程式設計指南'
ms.custom: seodec18
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
ms.openlocfilehash: a636fd35355dfa7320c2ca961ddada233c574dbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563154"
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="3eb17-102">&lt;list&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3eb17-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3eb17-103">語法</span><span class="sxs-lookup"><span data-stu-id="3eb17-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
#### <a name="parameters"></a><span data-ttu-id="3eb17-104">參數</span><span class="sxs-lookup"><span data-stu-id="3eb17-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="3eb17-105">要定義的詞彙，可定義於 `description` 中。</span><span class="sxs-lookup"><span data-stu-id="3eb17-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="3eb17-106">項目符號或編號清單中的項目或者 `term` 的定義。</span><span class="sxs-lookup"><span data-stu-id="3eb17-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb17-107">備註</span><span class="sxs-lookup"><span data-stu-id="3eb17-107">Remarks</span></span>  
 <span data-ttu-id="3eb17-108">\<listheader> 區塊用來定義資料表或定義清單的標題資料列。</span><span class="sxs-lookup"><span data-stu-id="3eb17-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="3eb17-109">定義資料表時，您只需要提供標題中詞彙的項目。</span><span class="sxs-lookup"><span data-stu-id="3eb17-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="3eb17-110">清單中的每個項目都是使用 \<item> 區塊所指定。</span><span class="sxs-lookup"><span data-stu-id="3eb17-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="3eb17-111">建立定義清單時，您需要同時指定 `term` 和 `description`。</span><span class="sxs-lookup"><span data-stu-id="3eb17-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="3eb17-112">不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。</span><span class="sxs-lookup"><span data-stu-id="3eb17-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3eb17-113">清單或資料表可以有所需的多個 \<item> 區塊。</span><span class="sxs-lookup"><span data-stu-id="3eb17-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="3eb17-114">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="3eb17-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eb17-115">範例</span><span class="sxs-lookup"><span data-stu-id="3eb17-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3eb17-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb17-116">See also</span></span>

- [<span data-ttu-id="3eb17-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3eb17-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3eb17-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="3eb17-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
