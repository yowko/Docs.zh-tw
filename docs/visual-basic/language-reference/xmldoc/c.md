---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400159"
---
# <a name="c-visual-basic"></a><span data-ttu-id="5f7aa-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f7aa-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="5f7aa-102">表示描述中的文字是程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7aa-103">語法</span><span class="sxs-lookup"><span data-stu-id="5f7aa-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f7aa-104">參數</span><span class="sxs-lookup"><span data-stu-id="5f7aa-104">Parameters</span></span>  
  
|<span data-ttu-id="5f7aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f7aa-105">Parameter</span></span>|<span data-ttu-id="5f7aa-106">說明</span><span class="sxs-lookup"><span data-stu-id="5f7aa-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="5f7aa-107">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7aa-108">備註</span><span class="sxs-lookup"><span data-stu-id="5f7aa-108">Remarks</span></span>  
 <span data-ttu-id="5f7aa-109">`<c>`標記可讓您指定描述中的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="5f7aa-110">用 [\<code>](code.md) 來指示多行作為程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="5f7aa-111">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f7aa-112">範例</span><span class="sxs-lookup"><span data-stu-id="5f7aa-112">Example</span></span>  
 <span data-ttu-id="5f7aa-113">這個範例會使用 `<c>` [摘要] 區段中的標記，來表示 `Counter` 是程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f7aa-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5f7aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f7aa-114">See also</span></span>

- [<span data-ttu-id="5f7aa-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="5f7aa-115">XML Comment Tags</span></span>](index.md)
