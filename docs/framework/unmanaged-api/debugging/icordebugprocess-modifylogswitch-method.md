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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b1c85499e5269027da2c2a01ab67aab2c5da626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775540"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="f5f05-102">ICorDebugProcess::ModifyLogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="f5f05-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="f5f05-103">設定指定的記錄參數的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="f5f05-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f05-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5f05-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f05-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5f05-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="f5f05-106">[in]指定的記錄參數名稱的字串指標。</span><span class="sxs-lookup"><span data-stu-id="f5f05-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="f5f05-107">[in]嚴重性層級設為指定的記錄參數。</span><span class="sxs-lookup"><span data-stu-id="f5f05-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5f05-108">備註</span><span class="sxs-lookup"><span data-stu-id="f5f05-108">Remarks</span></span>  
 <span data-ttu-id="f5f05-109">這個方法會有效之後，才[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼發生。</span><span class="sxs-lookup"><span data-stu-id="f5f05-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f05-110">需求</span><span class="sxs-lookup"><span data-stu-id="f5f05-110">Requirements</span></span>  
 <span data-ttu-id="f5f05-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5f05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f05-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5f05-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5f05-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5f05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5f05-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
