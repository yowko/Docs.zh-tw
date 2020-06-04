---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411495"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="40e90-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40e90-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="40e90-102">指定成員的摘要。</span><span class="sxs-lookup"><span data-stu-id="40e90-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e90-103">語法</span><span class="sxs-lookup"><span data-stu-id="40e90-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="40e90-104">參數</span><span class="sxs-lookup"><span data-stu-id="40e90-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="40e90-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="40e90-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40e90-106">備註</span><span class="sxs-lookup"><span data-stu-id="40e90-106">Remarks</span></span>  
 <span data-ttu-id="40e90-107">使用 `<summary>` 標記來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="40e90-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="40e90-108">使用將 [\<remarks>](remarks.md) 補充資訊加入至類型描述。</span><span class="sxs-lookup"><span data-stu-id="40e90-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="40e90-109">標記的文字 `<summary>` 是 IntelliSense 中類型的唯一資訊來源，也會顯示在物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="40e90-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="40e90-110">如需物件瀏覽器的相關資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="40e90-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="40e90-111">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="40e90-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40e90-112">範例</span><span class="sxs-lookup"><span data-stu-id="40e90-112">Example</span></span>  
 <span data-ttu-id="40e90-113">這個範例會使用 `<summary>` 標記來描述 `ResetCounter` 方法和 `Counter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="40e90-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40e90-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40e90-114">See also</span></span>

- [<span data-ttu-id="40e90-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="40e90-115">XML Comment Tags</span></span>](index.md)
