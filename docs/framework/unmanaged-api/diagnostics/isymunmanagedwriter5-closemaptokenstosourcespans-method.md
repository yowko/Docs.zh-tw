---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 43c35596d31842b85bbdc96a63413a176a59a172
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121647"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="d8977-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="d8977-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="d8977-103">關閉 [特殊自訂資料] 區段，以取得權杖對來源的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="d8977-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="d8977-104">關閉之後，就無法再新增任何對應資訊。</span><span class="sxs-lookup"><span data-stu-id="d8977-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8977-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8977-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d8977-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8977-106">Return Value</span></span>  
 <span data-ttu-id="d8977-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="d8977-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8977-108">需求</span><span class="sxs-lookup"><span data-stu-id="d8977-108">Requirements</span></span>  
 <span data-ttu-id="d8977-109">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d8977-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8977-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8977-110">See also</span></span>

- [<span data-ttu-id="d8977-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="d8977-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
