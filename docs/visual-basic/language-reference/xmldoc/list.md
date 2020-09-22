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
ms.openlocfilehash: 900cd8c467a21812d980cffa7e41120ae557704b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872781"
---
# <a name="list-visual-basic"></a><span data-ttu-id="7f9bc-101">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9bc-101">\<list> (Visual Basic)</span></span>

<span data-ttu-id="7f9bc-102">定義清單或資料表。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9bc-103">語法</span><span class="sxs-lookup"><span data-stu-id="7f9bc-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f9bc-104">參數</span><span class="sxs-lookup"><span data-stu-id="7f9bc-104">Parameters</span></span>  

 `type`  
 <span data-ttu-id="7f9bc-105">清單的類型。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-105">The type of the list.</span></span> <span data-ttu-id="7f9bc-106">必須是項目符號清單的「專案符號」、編號清單的「數位」，或兩個數據行資料表的「資料表」。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="7f9bc-107">只有在 `type` 為 "table" 時才會使用。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-107">Only used when `type` is "table."</span></span> <span data-ttu-id="7f9bc-108">要定義的詞彙，定義于 description 標記中。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="7f9bc-109">當是「 `type` 專案符號」或「數位」時，當 `description` 為 "Table" 時，清單中的專案是 `type` `description` 的定義 `term` 。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f9bc-110">備註</span><span class="sxs-lookup"><span data-stu-id="7f9bc-110">Remarks</span></span>  

 <span data-ttu-id="7f9bc-111">`<listheader>`區塊會定義資料表或定義清單的標題。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="7f9bc-112">定義資料表時，您只需要在標題中提供的專案 `term` 。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="7f9bc-113">清單中的每個專案都是以 `<item>` 區塊來指定。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="7f9bc-114">建立定義清單時，您必須同時指定 `term` 和 `description` 。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="7f9bc-115">不過，對於資料表、項目符號清單或編號清單，您只需要提供的專案 `description` 。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="7f9bc-116">清單或資料表可以視需要擁有多個 `<item>` 區塊。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="7f9bc-117">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9bc-118">範例</span><span class="sxs-lookup"><span data-stu-id="7f9bc-118">Example</span></span>  

 <span data-ttu-id="7f9bc-119">此範例會使用 `<list>` 標記來定義 [備註] 區段中的項目符號清單。</span><span class="sxs-lookup"><span data-stu-id="7f9bc-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9bc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9bc-120">See also</span></span>

- [<span data-ttu-id="7f9bc-121">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="7f9bc-121">XML Comment Tags</span></span>](index.md)
