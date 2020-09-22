---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 37b110cc6e12f11196d2a1c5cc6026d87b453626
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866414"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="06eba-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06eba-101">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="06eba-102">指定屬性或函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="06eba-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06eba-103">語法</span><span class="sxs-lookup"><span data-stu-id="06eba-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="06eba-104">參數</span><span class="sxs-lookup"><span data-stu-id="06eba-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="06eba-105">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="06eba-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06eba-106">備註</span><span class="sxs-lookup"><span data-stu-id="06eba-106">Remarks</span></span>  

 <span data-ttu-id="06eba-107">使用方法宣告的 `<returns>` 批註中的標記來描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="06eba-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="06eba-108">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="06eba-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06eba-109">範例</span><span class="sxs-lookup"><span data-stu-id="06eba-109">Example</span></span>  

 <span data-ttu-id="06eba-110">此範例會使用 `<returns>` 標記來說明函式傳回的內容 `DoesRecordExist` 。</span><span class="sxs-lookup"><span data-stu-id="06eba-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="06eba-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06eba-111">See also</span></span>

- [<span data-ttu-id="06eba-112">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="06eba-112">XML Comment Tags</span></span>](index.md)
