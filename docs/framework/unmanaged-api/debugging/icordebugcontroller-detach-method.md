---
title: ICorDebugController::Detach 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892907"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="1f74b-102">ICorDebugController::Detach 方法</span><span class="sxs-lookup"><span data-stu-id="1f74b-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="1f74b-103">從進程或應用程式域中卸離偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1f74b-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f74b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f74b-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f74b-105">備註</span><span class="sxs-lookup"><span data-stu-id="1f74b-105">Remarks</span></span>  
 <span data-ttu-id="1f74b-106">進程或應用程式域會繼續正常執行，但 "ICorDebugProcess" 或 "ICorDebugAppDomain" 物件不再有效，也不會再發生任何回呼。</span><span class="sxs-lookup"><span data-stu-id="1f74b-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="1f74b-107">在2.0 版的 .NET Framework 中，如果已啟用非受控的調試功能，此方法將會因為作業系統限制而失敗。</span><span class="sxs-lookup"><span data-stu-id="1f74b-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f74b-108">需求</span><span class="sxs-lookup"><span data-stu-id="1f74b-108">Requirements</span></span>  
 <span data-ttu-id="1f74b-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f74b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f74b-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f74b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f74b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f74b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f74b-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f74b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f74b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f74b-113">See also</span></span>
