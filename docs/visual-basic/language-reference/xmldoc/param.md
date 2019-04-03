---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4bcfe96361de9e196cb684ac4ba734f82442e25c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825556"
---
# <a name="param-visual-basic"></a><span data-ttu-id="6cc16-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cc16-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="6cc16-103">定義的參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="6cc16-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc16-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cc16-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cc16-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cc16-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6cc16-106">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6cc16-106">The name of a method parameter.</span></span> <span data-ttu-id="6cc16-107">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="6cc16-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6cc16-108">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="6cc16-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cc16-109">備註</span><span class="sxs-lookup"><span data-stu-id="6cc16-109">Remarks</span></span>  
 <span data-ttu-id="6cc16-110">`<param>`標記應該在方法宣告的註解中用來描述其中一個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="6cc16-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="6cc16-111">文字`<param>`標籤將會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="6cc16-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="6cc16-112">IntelliSense 的 參數資訊。</span><span class="sxs-lookup"><span data-stu-id="6cc16-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="6cc16-113">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="6cc16-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="6cc16-114">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6cc16-114">Object Browser.</span></span> <span data-ttu-id="6cc16-115">如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="6cc16-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="6cc16-116">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6cc16-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc16-117">範例</span><span class="sxs-lookup"><span data-stu-id="6cc16-117">Example</span></span>  
 <span data-ttu-id="6cc16-118">這個範例會使用`<param>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="6cc16-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6cc16-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cc16-119">See also</span></span>

- [<span data-ttu-id="6cc16-120">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="6cc16-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
