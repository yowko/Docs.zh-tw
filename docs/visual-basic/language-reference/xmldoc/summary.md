---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865837"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="941a5-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="941a5-101">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="941a5-102">指定成員的摘要。</span><span class="sxs-lookup"><span data-stu-id="941a5-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941a5-103">語法</span><span class="sxs-lookup"><span data-stu-id="941a5-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="941a5-104">參數</span><span class="sxs-lookup"><span data-stu-id="941a5-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="941a5-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="941a5-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="941a5-106">備註</span><span class="sxs-lookup"><span data-stu-id="941a5-106">Remarks</span></span>  

 <span data-ttu-id="941a5-107">使用 `<summary>` 標記來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="941a5-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="941a5-108">使用將 [\<remarks>](remarks.md) 補充資訊加入至類型描述。</span><span class="sxs-lookup"><span data-stu-id="941a5-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="941a5-109">標記的文字 `<summary>` 是 IntelliSense 中型別的唯一資訊來源，也會顯示在物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="941a5-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="941a5-110">如需物件瀏覽器的詳細資訊，請參閱 [查看程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="941a5-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="941a5-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="941a5-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="941a5-112">範例</span><span class="sxs-lookup"><span data-stu-id="941a5-112">Example</span></span>  

 <span data-ttu-id="941a5-113">此範例會使用 `<summary>` 標記來描述 `ResetCounter` 方法和 `Counter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="941a5-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="941a5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941a5-114">See also</span></span>

- [<span data-ttu-id="941a5-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="941a5-115">XML Comment Tags</span></span>](index.md)
