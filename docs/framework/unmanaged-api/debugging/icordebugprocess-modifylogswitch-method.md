---
title: ICorDebugProcess::ModifyLogSwitch 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139381"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="c7957-102">ICorDebugProcess::ModifyLogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="c7957-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="c7957-103">設定指定之記錄參數的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="c7957-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7957-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7957-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7957-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7957-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="c7957-106">在字串的指標，指定記錄參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7957-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="c7957-107">在要為指定的記錄參數設定的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="c7957-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7957-108">備註</span><span class="sxs-lookup"><span data-stu-id="c7957-108">Remarks</span></span>  
 <span data-ttu-id="c7957-109">只有在發生[ICorDebugManagedCallback：： CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼時，這個方法才有效。</span><span class="sxs-lookup"><span data-stu-id="c7957-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7957-110">需求</span><span class="sxs-lookup"><span data-stu-id="c7957-110">Requirements</span></span>  
 <span data-ttu-id="c7957-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7957-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7957-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7957-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7957-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7957-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7957-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7957-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
