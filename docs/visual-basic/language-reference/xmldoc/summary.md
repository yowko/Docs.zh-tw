---
title: '&lt;摘要&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 5ef9b7a98503ff36174de4418ca7d599c365f5aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671383"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="c7c73-102">&lt;摘要&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7c73-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="c7c73-103">指定成員的摘要。</span><span class="sxs-lookup"><span data-stu-id="c7c73-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c73-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7c73-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7c73-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7c73-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c7c73-106">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="c7c73-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7c73-107">備註</span><span class="sxs-lookup"><span data-stu-id="c7c73-107">Remarks</span></span>  
 <span data-ttu-id="c7c73-108">使用`<summary>`標記來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="c7c73-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="c7c73-109">使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 新增類型描述的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="c7c73-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="c7c73-110">文字`<summary>`標記在 IntelliSense 中類型的相關資訊的唯一來源，且也會顯示在 物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="c7c73-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="c7c73-111">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="c7c73-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="c7c73-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="c7c73-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7c73-113">範例</span><span class="sxs-lookup"><span data-stu-id="c7c73-113">Example</span></span>  
 <span data-ttu-id="c7c73-114">這個範例會使用`<summary>`標記來描述`ResetCounter`方法和`Counter`屬性。</span><span class="sxs-lookup"><span data-stu-id="c7c73-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c7c73-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7c73-115">See Also</span></span>  
 [<span data-ttu-id="c7c73-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="c7c73-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
