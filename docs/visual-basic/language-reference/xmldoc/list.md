---
title: <list>
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
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352313"
---
# <a name="list-visual-basic"></a><span data-ttu-id="5160a-101">\<清單 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5160a-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="5160a-102">定義清單或資料表。</span><span class="sxs-lookup"><span data-stu-id="5160a-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5160a-103">語法</span><span class="sxs-lookup"><span data-stu-id="5160a-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5160a-104">參數</span><span class="sxs-lookup"><span data-stu-id="5160a-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="5160a-105">清單的類型。</span><span class="sxs-lookup"><span data-stu-id="5160a-105">The type of the list.</span></span> <span data-ttu-id="5160a-106">必須是項目符號清單的「專案符號」、編號清單的「數位」，或是兩個數據行資料表的「資料表」。</span><span class="sxs-lookup"><span data-stu-id="5160a-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="5160a-107">只有在 `type` 為 "table" 時才會使用。</span><span class="sxs-lookup"><span data-stu-id="5160a-107">Only used when `type` is "table."</span></span> <span data-ttu-id="5160a-108">要定義的詞彙，定義于 description 標記中。</span><span class="sxs-lookup"><span data-stu-id="5160a-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="5160a-109">當 `type` 為「專案符號」或「數位」時，`description` 是 `type` 為 "table" 時清單中的專案，`description` 是 `term`的定義。</span><span class="sxs-lookup"><span data-stu-id="5160a-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5160a-110">備註</span><span class="sxs-lookup"><span data-stu-id="5160a-110">Remarks</span></span>  
 <span data-ttu-id="5160a-111">`<listheader>` 區塊會定義資料表或定義清單的標題。</span><span class="sxs-lookup"><span data-stu-id="5160a-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="5160a-112">定義資料表時，您只需要在標題中提供 `term` 的專案。</span><span class="sxs-lookup"><span data-stu-id="5160a-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="5160a-113">清單中的每個專案都是以 `<item>` 區塊來指定。</span><span class="sxs-lookup"><span data-stu-id="5160a-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="5160a-114">建立定義清單時，您必須同時指定 `term` 和 `description`。</span><span class="sxs-lookup"><span data-stu-id="5160a-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="5160a-115">不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description`的專案。</span><span class="sxs-lookup"><span data-stu-id="5160a-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="5160a-116">清單或資料表可以視需要擁有多個 `<item>` 區塊。</span><span class="sxs-lookup"><span data-stu-id="5160a-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="5160a-117">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5160a-117">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5160a-118">範例</span><span class="sxs-lookup"><span data-stu-id="5160a-118">Example</span></span>  
 <span data-ttu-id="5160a-119">這個範例會使用 `<list>` 標記，在 [備註] 區段中定義項目符號清單。</span><span class="sxs-lookup"><span data-stu-id="5160a-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5160a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5160a-120">See also</span></span>

- [<span data-ttu-id="5160a-121">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="5160a-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
