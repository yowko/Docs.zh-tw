---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871708"
---
# <a name="c-visual-basic"></a><span data-ttu-id="c39b5-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c39b5-101">\<c> (Visual Basic)</span></span>

<span data-ttu-id="c39b5-102">表示描述中的文字為程式碼。</span><span class="sxs-lookup"><span data-stu-id="c39b5-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39b5-103">語法</span><span class="sxs-lookup"><span data-stu-id="c39b5-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c39b5-104">參數</span><span class="sxs-lookup"><span data-stu-id="c39b5-104">Parameters</span></span>  
  
|<span data-ttu-id="c39b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="c39b5-105">Parameter</span></span>|<span data-ttu-id="c39b5-106">Description</span><span class="sxs-lookup"><span data-stu-id="c39b5-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="c39b5-107">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="c39b5-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c39b5-108">備註</span><span class="sxs-lookup"><span data-stu-id="c39b5-108">Remarks</span></span>  

 <span data-ttu-id="c39b5-109">`<c>`標記可讓您表示描述中的文字應標示為程式碼。</span><span class="sxs-lookup"><span data-stu-id="c39b5-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="c39b5-110">用 [\<code>](code.md) 來指出多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c39b5-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="c39b5-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="c39b5-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c39b5-112">範例</span><span class="sxs-lookup"><span data-stu-id="c39b5-112">Example</span></span>  

 <span data-ttu-id="c39b5-113">此範例會使用 `<c>` [摘要] 區段中的標記，指出這 `Counter` 是程式碼。</span><span class="sxs-lookup"><span data-stu-id="c39b5-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c39b5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c39b5-114">See also</span></span>

- [<span data-ttu-id="c39b5-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="c39b5-115">XML Comment Tags</span></span>](index.md)
