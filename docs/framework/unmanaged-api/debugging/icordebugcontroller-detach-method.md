---
title: "ICorDebugController::Detach 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="85c16-102">ICorDebugController::Detach 方法</span><span class="sxs-lookup"><span data-stu-id="85c16-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="85c16-103">從處理序或應用程式網域偵錯工具會中斷連結。</span><span class="sxs-lookup"><span data-stu-id="85c16-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c16-104">語法</span><span class="sxs-lookup"><span data-stu-id="85c16-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="85c16-105">備註</span><span class="sxs-lookup"><span data-stu-id="85c16-105">Remarks</span></span>  
 <span data-ttu-id="85c16-106">處理序或應用程式網域執行會繼續正常進行，但是"ICorDebugProcess"或"ICorDebugAppDomain"物件不再有效，而且沒有進一步的回呼就會發生。</span><span class="sxs-lookup"><span data-stu-id="85c16-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="85c16-107">在.NET Framework 2.0 版中，如果已啟用 unmanaged 偵錯，這個方法將會失敗由於作業系統限制。</span><span class="sxs-lookup"><span data-stu-id="85c16-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c16-108">需求</span><span class="sxs-lookup"><span data-stu-id="85c16-108">Requirements</span></span>  
 <span data-ttu-id="85c16-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85c16-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c16-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85c16-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85c16-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85c16-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85c16-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c16-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c16-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="85c16-113">See Also</span></span>  
 
