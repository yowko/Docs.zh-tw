---
title: <list> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 7d7b85867f4c701322c5e6c31f2d89ab38fad05d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940867"
---
# <a name="list-visual-basic"></a><span data-ttu-id="a3850-102">\<清單 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3850-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="a3850-103">定義清單或資料表。</span><span class="sxs-lookup"><span data-stu-id="a3850-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3850-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3850-104">Syntax</span></span>  
  
```xml  
<list type="type">  
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
  
## <a name="parameters"></a><span data-ttu-id="a3850-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3850-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="a3850-106">清單的類型。</span><span class="sxs-lookup"><span data-stu-id="a3850-106">The type of the list.</span></span> <span data-ttu-id="a3850-107">必須是"bullet"項目符號清單、 編號的清單，或兩個資料行資料表的 「 資料表 」 的 「 數字 」。</span><span class="sxs-lookup"><span data-stu-id="a3850-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="a3850-108">僅當使用`type`是 「 資料表 」。</span><span class="sxs-lookup"><span data-stu-id="a3850-108">Only used when `type` is "table."</span></span> <span data-ttu-id="a3850-109">要定義的詞彙，描述標記中定義。</span><span class="sxs-lookup"><span data-stu-id="a3850-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="a3850-110">當`type`"bullet"或"number"、`description`清單中的項目時`type`是 「 資料表 」`description`定義`term`。</span><span class="sxs-lookup"><span data-stu-id="a3850-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3850-111">備註</span><span class="sxs-lookup"><span data-stu-id="a3850-111">Remarks</span></span>  
 <span data-ttu-id="a3850-112">`<listheader>`區塊會定義資料表或定義清單的標題。</span><span class="sxs-lookup"><span data-stu-id="a3850-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="a3850-113">當定義資料表，您只需要提供的項目`term`標題中。</span><span class="sxs-lookup"><span data-stu-id="a3850-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="a3850-114">在清單中的每個項目指定`<item>`區塊。</span><span class="sxs-lookup"><span data-stu-id="a3850-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="a3850-115">在建立時定義 清單中，您必須同時指定`term`和`description`。</span><span class="sxs-lookup"><span data-stu-id="a3850-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="a3850-116">不過，針對資料表、 項目符號清單中或編號的清單中，您只需要提供的項目`description`。</span><span class="sxs-lookup"><span data-stu-id="a3850-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="a3850-117">清單或資料表可以有多個`<item>`封鎖所需。</span><span class="sxs-lookup"><span data-stu-id="a3850-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="a3850-118">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a3850-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3850-119">範例</span><span class="sxs-lookup"><span data-stu-id="a3850-119">Example</span></span>  
 <span data-ttu-id="a3850-120">這個範例會使用`<list>`標記來定義項目符號清單中的 < 備註 > 一節。</span><span class="sxs-lookup"><span data-stu-id="a3850-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a3850-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3850-121">See also</span></span>

- [<span data-ttu-id="a3850-122">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="a3850-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
