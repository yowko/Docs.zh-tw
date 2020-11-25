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
ms.openlocfilehash: 11ff430c426c93f1c2a5c0582495e089a33995fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709800"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="3e67f-102">ICorDebugModule2::SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="3e67f-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>

<span data-ttu-id="3e67f-103">設定旗標，這些旗標會控制此 ICorDebugModule2 的即時 (JIT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="3e67f-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e67f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e67f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e67f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e67f-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="3e67f-106">在 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="3e67f-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e67f-107">備註</span><span class="sxs-lookup"><span data-stu-id="3e67f-107">Remarks</span></span>  

 <span data-ttu-id="3e67f-108">如果 `dwFlags` 值無效， `SetJITCompilerFlags` 方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3e67f-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="3e67f-109">您 `SetJITCompilerFlags` 只能從這個模組的 [ICorDebugManagedCallback：： LoadModule](icordebugmanagedcallback-loadmodule-method.md) 回呼中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="3e67f-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="3e67f-110">在回呼傳遞之後嘗試呼叫它 `ICorDebugManagedCallback::LoadModule` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3e67f-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="3e67f-111">64位或 Win9x 平臺上不支援 [編輯後繼續]。</span><span class="sxs-lookup"><span data-stu-id="3e67f-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="3e67f-112">因此，如果您在 `SetJITCompilerFlags` 這兩個平臺的任一個上呼叫方法，並在中設定 CORDEBUG_JIT_ENABLE_ENC 旗標 `dwFlags` ，則此方法和 [編輯後繼續] 的特定方法（ `SetJITCompilerFlags` 例如 [ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md)）將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3e67f-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e67f-113">需求</span><span class="sxs-lookup"><span data-stu-id="3e67f-113">Requirements</span></span>  

 <span data-ttu-id="3e67f-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e67f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e67f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e67f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e67f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e67f-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e67f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
