---
title: ICorDebugMDA::GetFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a35e9f7cf43105db05408f285cd89dbd839a4cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969035"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="670bf-102">ICorDebugMDA::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="670bf-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="670bf-103">取得由 managed 偵錯助理 (MDA) 相關聯的旗標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="670bf-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="670bf-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="670bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="670bf-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="670bf-106">[in]位元組合[CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)列舉值，指定此 MDA 的旗標的設定。</span><span class="sxs-lookup"><span data-stu-id="670bf-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="670bf-107">需求</span><span class="sxs-lookup"><span data-stu-id="670bf-107">Requirements</span></span>  
 <span data-ttu-id="670bf-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="670bf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="670bf-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="670bf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="670bf-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="670bf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="670bf-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="670bf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670bf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="670bf-112">See also</span></span>

- [<span data-ttu-id="670bf-113">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="670bf-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="670bf-114">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="670bf-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
