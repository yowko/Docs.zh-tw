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
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792966"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="c9e1a-102">ICorDebugModule2::SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="c9e1a-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="c9e1a-103">設定可控制這個 ICorDebugModule2 之即時（JIT）編譯的旗標。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e1a-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9e1a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9e1a-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9e1a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="c9e1a-106">在[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9e1a-107">備註</span><span class="sxs-lookup"><span data-stu-id="c9e1a-107">Remarks</span></span>  
 <span data-ttu-id="c9e1a-108">如果 `dwFlags` 值無效，`SetJITCompilerFlags` 方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="c9e1a-109">只能從這個模組的[ICorDebugManagedCallback：： LoadModule](icordebugmanagedcallback-loadmodule-method.md)回呼中呼叫 `SetJITCompilerFlags` 方法。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="c9e1a-110">在傳遞 `ICorDebugManagedCallback::LoadModule` 回呼之後，嘗試呼叫它會失敗。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="c9e1a-111">64位或 Win9x 平臺不支援 [編輯後繼續]。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="c9e1a-112">因此，如果您在這兩個平臺的其中一個上呼叫 `SetJITCompilerFlags` 方法，並在 `dwFlags`中設定 CORDEBUG_JIT_ENABLE_ENC 旗標，`SetJITCompilerFlags` 方法和 [編輯後繼續] 特定的所有方法（例如[ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md)）將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e1a-113">需求</span><span class="sxs-lookup"><span data-stu-id="c9e1a-113">Requirements</span></span>  
 <span data-ttu-id="c9e1a-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9e1a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e1a-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9e1a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9e1a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9e1a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e1a-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e1a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
