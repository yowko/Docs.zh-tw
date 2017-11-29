---
title: "&lt;傳回&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="5265b-102">&lt;傳回&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5265b-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="5265b-103">指定屬性或函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="5265b-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5265b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5265b-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5265b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5265b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="5265b-106">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="5265b-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5265b-107">備註</span><span class="sxs-lookup"><span data-stu-id="5265b-107">Remarks</span></span>  
 <span data-ttu-id="5265b-108">使用`<returns>`標記來描述傳回值的方法宣告的註解中。</span><span class="sxs-lookup"><span data-stu-id="5265b-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="5265b-109">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5265b-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5265b-110">範例</span><span class="sxs-lookup"><span data-stu-id="5265b-110">Example</span></span>  
 <span data-ttu-id="5265b-111">這個範例會使用`<returns>`標記加入至說明`DoesRecordExist`函式會傳回。</span><span class="sxs-lookup"><span data-stu-id="5265b-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5265b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5265b-112">See Also</span></span>  
 [<span data-ttu-id="5265b-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="5265b-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
