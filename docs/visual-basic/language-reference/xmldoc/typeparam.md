---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 73ffb1319e6724a13a80b3cd1ca6985e4cbac05c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567057"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="1cf41-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf41-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="1cf41-103">定義的型別參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="1cf41-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf41-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cf41-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cf41-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cf41-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1cf41-106">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf41-106">The name of the type parameter.</span></span> <span data-ttu-id="1cf41-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf41-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="1cf41-108">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="1cf41-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cf41-109">備註</span><span class="sxs-lookup"><span data-stu-id="1cf41-109">Remarks</span></span>  
 <span data-ttu-id="1cf41-110">使用`<typeparam>`泛型類型或泛型成員宣告來描述的其中一個類型參數的註解中的標記。</span><span class="sxs-lookup"><span data-stu-id="1cf41-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="1cf41-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="1cf41-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cf41-112">範例</span><span class="sxs-lookup"><span data-stu-id="1cf41-112">Example</span></span>  
 <span data-ttu-id="1cf41-113">這個範例會使用`<typeparam>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="1cf41-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1cf41-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cf41-114">See also</span></span>
- [<span data-ttu-id="1cf41-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="1cf41-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
