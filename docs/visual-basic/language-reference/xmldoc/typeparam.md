---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b654fe6fc93642693730256b523fee999aa55937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="cd827-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd827-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="cd827-103">定義的型別參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="cd827-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd827-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd827-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd827-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd827-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="cd827-106">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd827-106">The name of the type parameter.</span></span> <span data-ttu-id="cd827-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="cd827-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="cd827-108">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="cd827-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd827-109">備註</span><span class="sxs-lookup"><span data-stu-id="cd827-109">Remarks</span></span>  
 <span data-ttu-id="cd827-110">使用`<typeparam>`泛型類型或泛型成員宣告描述的其中一個型別參數的註解中的標記。</span><span class="sxs-lookup"><span data-stu-id="cd827-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="cd827-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="cd827-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd827-112">範例</span><span class="sxs-lookup"><span data-stu-id="cd827-112">Example</span></span>  
 <span data-ttu-id="cd827-113">這個範例會使用`<typeparam>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="cd827-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cd827-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd827-114">See Also</span></span>  
 [<span data-ttu-id="cd827-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="cd827-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
