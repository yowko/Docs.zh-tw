---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524030"
---
# <a name="code-visual-basic"></a><span data-ttu-id="f1d66-101">\<code > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f1d66-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="f1d66-102">表示文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1d66-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d66-103">語法</span><span class="sxs-lookup"><span data-stu-id="f1d66-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1d66-104">參數</span><span class="sxs-lookup"><span data-stu-id="f1d66-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="f1d66-105">要標示為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="f1d66-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1d66-106">備註</span><span class="sxs-lookup"><span data-stu-id="f1d66-106">Remarks</span></span>  
 <span data-ttu-id="f1d66-107">使用 `<code>` 標記，將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1d66-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="f1d66-108">[\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="f1d66-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="f1d66-109">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="f1d66-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1d66-110">範例</span><span class="sxs-lookup"><span data-stu-id="f1d66-110">Example</span></span>  
 <span data-ttu-id="f1d66-111">這個範例會使用 \<code > 標記，以包含使用 [`ID`] 欄位的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1d66-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f1d66-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1d66-112">See also</span></span>

- [<span data-ttu-id="f1d66-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="f1d66-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
