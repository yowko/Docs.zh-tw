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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f687e48413cb227ad715720e24bd645065309553
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748852"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="5fb08-102">ICorDebugController::Detach 方法</span><span class="sxs-lookup"><span data-stu-id="5fb08-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="5fb08-103">中斷連結處理序或應用程式定義域與偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5fb08-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb08-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fb08-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5fb08-105">備註</span><span class="sxs-lookup"><span data-stu-id="5fb08-105">Remarks</span></span>  
 <span data-ttu-id="5fb08-106">處理序或應用程式網域執行會繼續正常執行，但 「 ICorDebugProcess"或"ICorDebugAppDomain 「 物件已不再有效，就會發生任何進一步的回呼。</span><span class="sxs-lookup"><span data-stu-id="5fb08-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="5fb08-107">在.NET Framework 2.0 版中，如果已啟用 unmanaged 偵錯，這個方法將會失敗由於作業系統限制。</span><span class="sxs-lookup"><span data-stu-id="5fb08-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb08-108">需求</span><span class="sxs-lookup"><span data-stu-id="5fb08-108">Requirements</span></span>  
 <span data-ttu-id="5fb08-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb08-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb08-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb08-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb08-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb08-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fb08-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb08-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb08-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fb08-113">See also</span></span>
