---
title: <param> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524727"
---
# <a name="param-visual-basic"></a><span data-ttu-id="19f22-102">\<param > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="19f22-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="19f22-103">定義參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="19f22-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f22-104">語法</span><span class="sxs-lookup"><span data-stu-id="19f22-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="19f22-105">參數</span><span class="sxs-lookup"><span data-stu-id="19f22-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="19f22-106">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="19f22-106">The name of a method parameter.</span></span> <span data-ttu-id="19f22-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="19f22-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="19f22-108">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="19f22-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19f22-109">備註</span><span class="sxs-lookup"><span data-stu-id="19f22-109">Remarks</span></span>  
 <span data-ttu-id="19f22-110">@No__t_0 標記應該用於方法宣告的批註中，以描述方法的其中一個參數。</span><span class="sxs-lookup"><span data-stu-id="19f22-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="19f22-111">@No__t_0 標記的文字會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="19f22-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="19f22-112">IntelliSense 的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="19f22-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="19f22-113">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="19f22-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="19f22-114">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="19f22-114">Object Browser.</span></span> <span data-ttu-id="19f22-115">如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="19f22-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="19f22-116">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="19f22-116">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19f22-117">範例</span><span class="sxs-lookup"><span data-stu-id="19f22-117">Example</span></span>  
 <span data-ttu-id="19f22-118">這個範例會使用 `<param>` 標記來描述 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="19f22-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="19f22-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="19f22-119">See also</span></span>

- [<span data-ttu-id="19f22-120">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="19f22-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
