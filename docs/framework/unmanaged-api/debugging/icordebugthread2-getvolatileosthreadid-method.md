---
title: ICorDebugThread2::GetVolatileOSThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d964a5a77569762ff4fd69e419324a377b820d97
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768941"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="d193f-102">ICorDebugThread2::GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="d193f-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="d193f-103">取得此 ICorDebugThread2 作業系統執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="d193f-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d193f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d193f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d193f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d193f-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="d193f-106">[out]此執行緒的作業系統執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="d193f-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d193f-107">需求</span><span class="sxs-lookup"><span data-stu-id="d193f-107">Requirements</span></span>  
 <span data-ttu-id="d193f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d193f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d193f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d193f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d193f-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d193f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d193f-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d193f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
