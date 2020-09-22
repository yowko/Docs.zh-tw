---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873023"
---
# <a name="code-visual-basic"></a><span data-ttu-id="0d0b1-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d0b1-101">\<code> (Visual Basic)</span></span>

<span data-ttu-id="0d0b1-102">表示文字是多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0b1-103">語法</span><span class="sxs-lookup"><span data-stu-id="0d0b1-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0b1-104">參數</span><span class="sxs-lookup"><span data-stu-id="0d0b1-104">Parameters</span></span>  

 `content`  
 <span data-ttu-id="0d0b1-105">要標示為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0b1-106">備註</span><span class="sxs-lookup"><span data-stu-id="0d0b1-106">Remarks</span></span>  

 <span data-ttu-id="0d0b1-107">使用 `<code>` 標記以程式碼表示多行。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="0d0b1-108">用 [\<c>](c.md) 來表示描述中的文字應標示為程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="0d0b1-109">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0b1-110">範例</span><span class="sxs-lookup"><span data-stu-id="0d0b1-110">Example</span></span>  

 <span data-ttu-id="0d0b1-111">此範例會使用 \<code> 標記來包含使用欄位的範例程式碼 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="0d0b1-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0d0b1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d0b1-112">See also</span></span>

- [<span data-ttu-id="0d0b1-113">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="0d0b1-113">XML Comment Tags</span></span>](index.md)
