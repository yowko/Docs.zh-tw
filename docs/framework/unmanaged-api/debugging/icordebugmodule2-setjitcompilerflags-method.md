---
title: ICorDebugModule2::SetJITCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114f4ff261d9612a81d17bf5b3df2f87323f77f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764197"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="596fa-102">ICorDebugModule2::SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="596fa-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="596fa-103">設定控制此 ICorDebugModule2-just-in-time (JIT) 編譯旗標。</span><span class="sxs-lookup"><span data-stu-id="596fa-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="596fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="596fa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="596fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="596fa-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="596fa-106">[in]位元組合[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="596fa-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="596fa-107">備註</span><span class="sxs-lookup"><span data-stu-id="596fa-107">Remarks</span></span>  
 <span data-ttu-id="596fa-108">如果`dwFlags`值無效，`SetJITCompilerFlags`方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="596fa-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="596fa-109">`SetJITCompilerFlags`方法可以呼叫內[icordebugmanagedcallback:: Loadmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)此模組的回呼。</span><span class="sxs-lookup"><span data-stu-id="596fa-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="596fa-110">嘗試呼叫之後`ICorDebugManagedCallback::LoadModule`傳遞回呼將會失敗。</span><span class="sxs-lookup"><span data-stu-id="596fa-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="596fa-111">64 位元或 Win9x 平台上不支援編輯後繼續。</span><span class="sxs-lookup"><span data-stu-id="596fa-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="596fa-112">因此，如果您呼叫`SetJITCompilerFlags`CORDEBUG_JIT_ENABLE_ENC 旗標中設定這些兩個平台上的方法`dwFlags`，則`SetJITCompilerFlags`方法和特定的所有方法，以編輯後繼續，例如[ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)，將會失敗。</span><span class="sxs-lookup"><span data-stu-id="596fa-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="596fa-113">需求</span><span class="sxs-lookup"><span data-stu-id="596fa-113">Requirements</span></span>  
 <span data-ttu-id="596fa-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="596fa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="596fa-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="596fa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="596fa-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="596fa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="596fa-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="596fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
