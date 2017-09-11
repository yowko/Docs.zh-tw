---
title: "&lt;摘要&gt;(Visual Basic) |Microsoft 文件"
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
ms.openlocfilehash: 42321daf092c4b637d2f75fb7f6d7e95201791ba
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017

---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="5add1-102">&lt;摘要&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5add1-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="5add1-103">指定成員的摘要。</span><span class="sxs-lookup"><span data-stu-id="5add1-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5add1-104">語法</span><span class="sxs-lookup"><span data-stu-id="5add1-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5add1-105">參數</span><span class="sxs-lookup"><span data-stu-id="5add1-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="5add1-106">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="5add1-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5add1-107">備註</span><span class="sxs-lookup"><span data-stu-id="5add1-107">Remarks</span></span>  
 <span data-ttu-id="5add1-108">使用`<summary>`標記，來說明型別或型別成員。</span><span class="sxs-lookup"><span data-stu-id="5add1-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="5add1-109">使用[\<註解 >](../../../visual-basic/language-reference/xmldoc/remarks.md)加入類型描述的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="5add1-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="5add1-110">文字`<summary>`標記是唯一的來源中的 IntelliSense，類型的相關資訊，也會顯示在 物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="5add1-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="5add1-111">物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="5add1-111">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="5add1-112">使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5add1-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5add1-113">範例</span><span class="sxs-lookup"><span data-stu-id="5add1-113">Example</span></span>  
 <span data-ttu-id="5add1-114">這個範例會使用`<summary>`標記，來說明`ResetCounter`方法和`Counter`屬性。</span><span class="sxs-lookup"><span data-stu-id="5add1-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 <span data-ttu-id="5add1-115">[!code-vb[VbVbcnXmlDocComments #&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5add1-115">[!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5add1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5add1-116">See Also</span></span>  
 [<span data-ttu-id="5add1-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="5add1-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
