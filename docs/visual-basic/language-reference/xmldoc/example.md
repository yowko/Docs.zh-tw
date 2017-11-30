---
title: "&lt;範例&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e34b75f4ce924a35dd5396b449730316025a9f35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltexamplegt-visual-basic"></a><span data-ttu-id="c176e-102">&lt;範例&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c176e-102">&lt;example&gt; (Visual Basic)</span></span>
<span data-ttu-id="c176e-103">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="c176e-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c176e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c176e-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c176e-105">參數</span><span class="sxs-lookup"><span data-stu-id="c176e-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c176e-106">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="c176e-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c176e-107">備註</span><span class="sxs-lookup"><span data-stu-id="c176e-107">Remarks</span></span>  
 <span data-ttu-id="c176e-108">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="c176e-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="c176e-109">這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="c176e-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="c176e-110">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="c176e-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c176e-111">範例</span><span class="sxs-lookup"><span data-stu-id="c176e-111">Example</span></span>  
 <span data-ttu-id="c176e-112">這個範例會使用`<example>`標記来包含的範例使用`ID`欄位。</span><span class="sxs-lookup"><span data-stu-id="c176e-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c176e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c176e-113">See Also</span></span>  
 [<span data-ttu-id="c176e-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="c176e-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
