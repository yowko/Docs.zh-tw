---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411482"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="d326a-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d326a-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="d326a-102">定義類型參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="d326a-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d326a-103">語法</span><span class="sxs-lookup"><span data-stu-id="d326a-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d326a-104">參數</span><span class="sxs-lookup"><span data-stu-id="d326a-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d326a-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d326a-105">The name of the type parameter.</span></span> <span data-ttu-id="d326a-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="d326a-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d326a-107">類型參數的描述。</span><span class="sxs-lookup"><span data-stu-id="d326a-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d326a-108">備註</span><span class="sxs-lookup"><span data-stu-id="d326a-108">Remarks</span></span>  
 <span data-ttu-id="d326a-109">在 `<typeparam>` 泛型型別或泛型成員宣告的批註中使用標記，以描述其中一個類型參數。</span><span class="sxs-lookup"><span data-stu-id="d326a-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="d326a-110">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="d326a-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d326a-111">範例</span><span class="sxs-lookup"><span data-stu-id="d326a-111">Example</span></span>  
 <span data-ttu-id="d326a-112">這個範例會使用 `<typeparam>` 標記來描述 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="d326a-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d326a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d326a-113">See also</span></span>

- [<span data-ttu-id="d326a-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="d326a-114">XML Comment Tags</span></span>](index.md)
