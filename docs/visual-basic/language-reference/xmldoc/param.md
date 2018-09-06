---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4cb3de06d574f8b9abb3e3e11641a6ada750b56a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856487"
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="7130a-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7130a-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="7130a-103">定義的參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="7130a-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7130a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7130a-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7130a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7130a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7130a-106">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7130a-106">The name of a method parameter.</span></span> <span data-ttu-id="7130a-107">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="7130a-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="7130a-108">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="7130a-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7130a-109">備註</span><span class="sxs-lookup"><span data-stu-id="7130a-109">Remarks</span></span>  
 <span data-ttu-id="7130a-110">`<param>`標記應該在方法宣告的註解中用來描述其中一個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="7130a-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="7130a-111">文字`<param>`標籤將會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="7130a-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="7130a-112">IntelliSense 的 參數資訊。</span><span class="sxs-lookup"><span data-stu-id="7130a-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="7130a-113">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="7130a-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="7130a-114">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="7130a-114">Object Browser.</span></span> <span data-ttu-id="7130a-115">如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="7130a-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="7130a-116">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="7130a-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7130a-117">範例</span><span class="sxs-lookup"><span data-stu-id="7130a-117">Example</span></span>  
 <span data-ttu-id="7130a-118">這個範例會使用`<param>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="7130a-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7130a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7130a-119">See Also</span></span>  
 [<span data-ttu-id="7130a-120">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="7130a-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
