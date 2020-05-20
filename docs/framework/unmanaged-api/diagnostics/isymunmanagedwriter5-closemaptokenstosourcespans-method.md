---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 053727604c795bf43a9b1658d5841fe85f53090a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614626"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="48efd-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="48efd-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="48efd-103">關閉 [特殊自訂資料] 區段，以取得權杖對來源的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="48efd-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="48efd-104">關閉之後，就無法再新增任何對應資訊。</span><span class="sxs-lookup"><span data-stu-id="48efd-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48efd-105">語法</span><span class="sxs-lookup"><span data-stu-id="48efd-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="48efd-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="48efd-106">Return Value</span></span>  
 <span data-ttu-id="48efd-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="48efd-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48efd-108">需求</span><span class="sxs-lookup"><span data-stu-id="48efd-108">Requirements</span></span>  
 <span data-ttu-id="48efd-109">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="48efd-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48efd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48efd-110">See also</span></span>

- [<span data-ttu-id="48efd-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="48efd-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
