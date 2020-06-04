---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400136"
---
# <a name="code-visual-basic"></a><span data-ttu-id="79475-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79475-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="79475-102">表示文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="79475-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79475-103">語法</span><span class="sxs-lookup"><span data-stu-id="79475-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="79475-104">參數</span><span class="sxs-lookup"><span data-stu-id="79475-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="79475-105">要標示為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="79475-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79475-106">備註</span><span class="sxs-lookup"><span data-stu-id="79475-106">Remarks</span></span>  
 <span data-ttu-id="79475-107">使用 `<code>` 標記，將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="79475-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="79475-108">用 [\<c>](c.md) 來表示描述中的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="79475-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="79475-109">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="79475-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79475-110">範例</span><span class="sxs-lookup"><span data-stu-id="79475-110">Example</span></span>  
 <span data-ttu-id="79475-111">這個範例會使用 \<code> 標記來包含使用欄位的範例程式碼 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="79475-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="79475-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79475-112">See also</span></span>

- [<span data-ttu-id="79475-113">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="79475-113">XML Comment Tags</span></span>](index.md)
