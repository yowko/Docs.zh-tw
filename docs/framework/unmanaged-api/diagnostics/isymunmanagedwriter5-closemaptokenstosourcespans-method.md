---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f8a89532999f599c8ec595fa709044b7d13a53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="23965-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="23965-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="23965-103">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="23965-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="23965-104">它已關閉之後，就可以加入沒有對應的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="23965-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23965-105">語法</span><span class="sxs-lookup"><span data-stu-id="23965-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="23965-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="23965-106">Return Value</span></span>  
 <span data-ttu-id="23965-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="23965-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23965-108">需求</span><span class="sxs-lookup"><span data-stu-id="23965-108">Requirements</span></span>  
 <span data-ttu-id="23965-109">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23965-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23965-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="23965-110">See Also</span></span>  
 [<span data-ttu-id="23965-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="23965-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
