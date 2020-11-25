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
ms.openlocfilehash: 55acb6e3ec60925cba3d8aa5328547c54f270356
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732667"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="7f86a-102">ICorDebugController::Detach 方法</span><span class="sxs-lookup"><span data-stu-id="7f86a-102">ICorDebugController::Detach Method</span></span>

<span data-ttu-id="7f86a-103">卸離進程或應用程式域中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7f86a-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f86a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f86a-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7f86a-105">備註</span><span class="sxs-lookup"><span data-stu-id="7f86a-105">Remarks</span></span>  

 <span data-ttu-id="7f86a-106">進程或應用程式域會繼續正常執行，但 "ICorDebugProcess" 或 "ICorDebugAppDomain" 物件不再有效，且不會再發生任何回呼。</span><span class="sxs-lookup"><span data-stu-id="7f86a-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="7f86a-107">在 .NET Framework 2.0 版中，如果已啟用非受控的偵錯工具，此方法將會因為作業系統限制而失敗。</span><span class="sxs-lookup"><span data-stu-id="7f86a-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f86a-108">需求</span><span class="sxs-lookup"><span data-stu-id="7f86a-108">Requirements</span></span>  

 <span data-ttu-id="7f86a-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f86a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f86a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f86a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f86a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f86a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f86a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f86a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f86a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f86a-113">See also</span></span>
