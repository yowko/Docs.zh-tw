---
title: ICorDebugProcess::EnableLogMessages 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b199d3226ec391fadc356b5efacdbf10a3e25adf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766166"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="e8565-102">ICorDebugProcess::EnableLogMessages 方法</span><span class="sxs-lookup"><span data-stu-id="e8565-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="e8565-103">啟用和停用偵錯工具的記錄檔訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="e8565-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8565-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8565-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8565-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8565-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="e8565-106">[in]`true`啟用傳輸記錄檔訊息;`false`停用傳輸。</span><span class="sxs-lookup"><span data-stu-id="e8565-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8565-107">備註</span><span class="sxs-lookup"><span data-stu-id="e8565-107">Remarks</span></span>  
 <span data-ttu-id="e8565-108">這個方法會有效之後，才[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼，就會發生。</span><span class="sxs-lookup"><span data-stu-id="e8565-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8565-109">需求</span><span class="sxs-lookup"><span data-stu-id="e8565-109">Requirements</span></span>  
 <span data-ttu-id="e8565-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8565-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8565-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8565-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8565-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8565-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8565-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8565-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
