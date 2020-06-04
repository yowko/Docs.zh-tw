---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399991"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="0fff7-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fff7-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="0fff7-102">指定屬性或函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="0fff7-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fff7-103">語法</span><span class="sxs-lookup"><span data-stu-id="0fff7-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fff7-104">參數</span><span class="sxs-lookup"><span data-stu-id="0fff7-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0fff7-105">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="0fff7-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fff7-106">備註</span><span class="sxs-lookup"><span data-stu-id="0fff7-106">Remarks</span></span>  
 <span data-ttu-id="0fff7-107">`<returns>`在方法宣告的批註中使用標記，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="0fff7-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="0fff7-108">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="0fff7-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fff7-109">範例</span><span class="sxs-lookup"><span data-stu-id="0fff7-109">Example</span></span>  
 <span data-ttu-id="0fff7-110">這個範例會使用 `<returns>` 標記來說明函式所傳回的內容 `DoesRecordExist` 。</span><span class="sxs-lookup"><span data-stu-id="0fff7-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0fff7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fff7-111">See also</span></span>

- [<span data-ttu-id="0fff7-112">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="0fff7-112">XML Comment Tags</span></span>](index.md)
