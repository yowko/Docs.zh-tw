---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354316"
---
# <a name="code-visual-basic"></a><span data-ttu-id="c7fd3-101">\<程式碼 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c7fd3-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="c7fd3-102">表示文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7fd3-103">語法</span><span class="sxs-lookup"><span data-stu-id="c7fd3-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7fd3-104">參數</span><span class="sxs-lookup"><span data-stu-id="c7fd3-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="c7fd3-105">要標示為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7fd3-106">備註</span><span class="sxs-lookup"><span data-stu-id="c7fd3-106">Remarks</span></span>  
 <span data-ttu-id="c7fd3-107">使用 `<code>` 標記，將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="c7fd3-108">[\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="c7fd3-109">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7fd3-110">範例</span><span class="sxs-lookup"><span data-stu-id="c7fd3-110">Example</span></span>  
 <span data-ttu-id="c7fd3-111">這個範例會使用 \<的程式碼 > 標記，以包含使用 [`ID`] 欄位的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c7fd3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7fd3-112">See also</span></span>

- [<span data-ttu-id="c7fd3-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="c7fd3-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
