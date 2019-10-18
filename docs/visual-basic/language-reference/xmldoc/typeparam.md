---
title: <typeparam> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524617"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="70b4f-102">\<typeparam > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="70b4f-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="70b4f-103">定義類型參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="70b4f-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70b4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="70b4f-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="70b4f-105">參數</span><span class="sxs-lookup"><span data-stu-id="70b4f-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="70b4f-106">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="70b4f-106">The name of the type parameter.</span></span> <span data-ttu-id="70b4f-107">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="70b4f-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="70b4f-108">類型參數的描述。</span><span class="sxs-lookup"><span data-stu-id="70b4f-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70b4f-109">備註</span><span class="sxs-lookup"><span data-stu-id="70b4f-109">Remarks</span></span>  
 <span data-ttu-id="70b4f-110">在泛型型別或泛型成員宣告的批註中使用 `<typeparam>` 標記，以描述其中一個類型參數。</span><span class="sxs-lookup"><span data-stu-id="70b4f-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="70b4f-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="70b4f-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b4f-112">範例</span><span class="sxs-lookup"><span data-stu-id="70b4f-112">Example</span></span>  
 <span data-ttu-id="70b4f-113">這個範例會使用 `<typeparam>` 標記來描述 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="70b4f-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="70b4f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="70b4f-114">See also</span></span>

- [<span data-ttu-id="70b4f-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="70b4f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
