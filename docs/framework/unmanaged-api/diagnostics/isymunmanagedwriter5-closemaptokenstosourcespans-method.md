---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: b57174f9f76b174927b8f1997beac3dd1482583a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725907"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="af9ff-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="af9ff-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="af9ff-103">針對權杖對來源範圍的對應資訊，關閉特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="af9ff-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="af9ff-104">關閉之後，就無法再加入任何對應資訊。</span><span class="sxs-lookup"><span data-stu-id="af9ff-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9ff-105">語法</span><span class="sxs-lookup"><span data-stu-id="af9ff-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="af9ff-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="af9ff-106">Return Value</span></span>  

 <span data-ttu-id="af9ff-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="af9ff-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9ff-108">需求</span><span class="sxs-lookup"><span data-stu-id="af9ff-108">Requirements</span></span>  

 <span data-ttu-id="af9ff-109">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="af9ff-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9ff-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af9ff-110">See also</span></span>

- [<span data-ttu-id="af9ff-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="af9ff-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
