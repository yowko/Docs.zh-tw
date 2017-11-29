---
title: '&lt;paramref&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3bf3d4f04997a03f442cf7fd2a1586604198d3fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="d30e5-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d30e5-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="d30e5-103">格式化文字，做為參數。</span><span class="sxs-lookup"><span data-stu-id="d30e5-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d30e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d30e5-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d30e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="d30e5-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d30e5-106">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d30e5-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="d30e5-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="d30e5-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d30e5-108">備註</span><span class="sxs-lookup"><span data-stu-id="d30e5-108">Remarks</span></span>  
 <span data-ttu-id="d30e5-109">`<paramref>`標籤會提供一個方法來指示一個字是參數。</span><span class="sxs-lookup"><span data-stu-id="d30e5-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="d30e5-110">可以處理 XML 檔案，以醒目的方式格式化此參數。</span><span class="sxs-lookup"><span data-stu-id="d30e5-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="d30e5-111">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="d30e5-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d30e5-112">範例</span><span class="sxs-lookup"><span data-stu-id="d30e5-112">Example</span></span>  
 <span data-ttu-id="d30e5-113">這個範例會使用`<paramref>`標記來參考`id`參數。</span><span class="sxs-lookup"><span data-stu-id="d30e5-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d30e5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d30e5-114">See Also</span></span>  
 [<span data-ttu-id="d30e5-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="d30e5-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
