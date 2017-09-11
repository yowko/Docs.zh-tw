---
title: "&lt;param&gt; (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: ddf5baf83816d757edf67cdf1c66dc24e4313b83
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017

---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="80910-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80910-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="80910-103">定義的參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="80910-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80910-104">語法</span><span class="sxs-lookup"><span data-stu-id="80910-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80910-105">參數</span><span class="sxs-lookup"><span data-stu-id="80910-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="80910-106">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="80910-106">The name of a method parameter.</span></span> <span data-ttu-id="80910-107">將名稱括在雙引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="80910-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="80910-108">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="80910-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80910-109">備註</span><span class="sxs-lookup"><span data-stu-id="80910-109">Remarks</span></span>  
 <span data-ttu-id="80910-110">`<param>`標記應使用於方法宣告的註解來描述的其中一個方法參數。</span><span class="sxs-lookup"><span data-stu-id="80910-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="80910-111">文字`<param>`標記會出現在下列位置︰</span><span class="sxs-lookup"><span data-stu-id="80910-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="80910-112">IntelliSense 的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="80910-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="80910-113">如需詳細資訊，請參閱[使用 IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="80910-113">For more information, see [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="80910-114">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="80910-114">Object Browser.</span></span> <span data-ttu-id="80910-115">如需詳細資訊，請參閱[檢視程式碼的結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="80910-115">For more information, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="80910-116">使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="80910-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80910-117">範例</span><span class="sxs-lookup"><span data-stu-id="80910-117">Example</span></span>  
 <span data-ttu-id="80910-118">這個範例會使用`<param>`標記，來說明`id`參數。</span><span class="sxs-lookup"><span data-stu-id="80910-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 <span data-ttu-id="80910-119">[!code-vb[VbVbcnXmlDocComments #&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="80910-119">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80910-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80910-120">See Also</span></span>  
 [<span data-ttu-id="80910-121">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="80910-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
