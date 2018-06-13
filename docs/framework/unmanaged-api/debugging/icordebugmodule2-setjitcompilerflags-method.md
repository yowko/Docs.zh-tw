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
ms.openlocfilehash: e605859a3049abc0c17d9d6792ade78f4ad2bd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417358"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="13568-102">ICorDebugModule2::SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="13568-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="13568-103">設定控制此 ICorDebugModule2 在 just-in-time (JIT) 編譯的旗標。</span><span class="sxs-lookup"><span data-stu-id="13568-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13568-104">語法</span><span class="sxs-lookup"><span data-stu-id="13568-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13568-105">參數</span><span class="sxs-lookup"><span data-stu-id="13568-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="13568-106">[in]位元組合[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="13568-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13568-107">備註</span><span class="sxs-lookup"><span data-stu-id="13568-107">Remarks</span></span>  
 <span data-ttu-id="13568-108">如果`dwFlags`值無效，`SetJITCompilerFlags`方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="13568-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="13568-109">`SetJITCompilerFlags`可以呼叫方法，只能從[icordebugmanagedcallback:: Loadmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)針對此模組的回呼。</span><span class="sxs-lookup"><span data-stu-id="13568-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="13568-110">嘗試呼叫之後`ICorDebugManagedCallback::LoadModule`傳遞回呼將會失敗。</span><span class="sxs-lookup"><span data-stu-id="13568-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="13568-111">64 位元或 Win9x 平台上不支援編輯後繼續。</span><span class="sxs-lookup"><span data-stu-id="13568-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="13568-112">因此，如果您呼叫`SetJITCompilerFlags`方法上其中一個 CORDEBUG_JIT_ENABLE_ENC 旗標設定兩個平台`dwFlags`、`SetJITCompilerFlags`方法和所有方法的特定編輯後繼續，例如[ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)，將會失敗。</span><span class="sxs-lookup"><span data-stu-id="13568-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13568-113">需求</span><span class="sxs-lookup"><span data-stu-id="13568-113">Requirements</span></span>  
 <span data-ttu-id="13568-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13568-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13568-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13568-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13568-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13568-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13568-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13568-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
