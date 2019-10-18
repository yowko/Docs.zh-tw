---
title: <returns> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524691"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="fe38f-102">\<returns > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="fe38f-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="fe38f-103">指定屬性或函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="fe38f-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe38f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe38f-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe38f-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe38f-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="fe38f-106">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="fe38f-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe38f-107">備註</span><span class="sxs-lookup"><span data-stu-id="fe38f-107">Remarks</span></span>  
 <span data-ttu-id="fe38f-108">在方法宣告的批註中使用 `<returns>` 標記，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="fe38f-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="fe38f-109">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="fe38f-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe38f-110">範例</span><span class="sxs-lookup"><span data-stu-id="fe38f-110">Example</span></span>  
 <span data-ttu-id="fe38f-111">這個範例會使用 `<returns>` 標記來說明 `DoesRecordExist` 函數傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="fe38f-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fe38f-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe38f-112">See also</span></span>

- [<span data-ttu-id="fe38f-113">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="fe38f-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
