---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3582ebf2acee02d49aabafb03604c84249c4ce13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747383"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="60ba1-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="60ba1-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="60ba1-103">設定必須內嵌在先行編譯的映像，以便將該映像載入目前的程序的執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="60ba1-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ba1-104">語法</span><span class="sxs-lookup"><span data-stu-id="60ba1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ba1-105">參數</span><span class="sxs-lookup"><span data-stu-id="60ba1-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="60ba1-106">[in]值為[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定的編譯器旗標用來選取正確的先行編譯映像。</span><span class="sxs-lookup"><span data-stu-id="60ba1-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60ba1-107">備註</span><span class="sxs-lookup"><span data-stu-id="60ba1-107">Remarks</span></span>  
 <span data-ttu-id="60ba1-108">`SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯的映像中，以便在執行階段會載入此程序的該映像的旗標。</span><span class="sxs-lookup"><span data-stu-id="60ba1-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="60ba1-109">這個方法所設定的旗標是只能用來選取正確的先行編譯映像。</span><span class="sxs-lookup"><span data-stu-id="60ba1-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="60ba1-110">如果沒有這類映像存在時，執行階段將 Microsoft intermediate language (MSIL) 映像，而且在 just-in-time (JIT) 編譯器改為載入。</span><span class="sxs-lookup"><span data-stu-id="60ba1-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="60ba1-111">在此情況下，仍然必須使用偵錯工具[ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法，以進行 JIT 編譯，視需要設定之旗標。</span><span class="sxs-lookup"><span data-stu-id="60ba1-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="60ba1-112">如果已載入的映像，但一些 JIT 編譯必須進行該映像 （這會是大小寫，如果映像包含泛型），所指定的編譯器旗標`SetDesiredNGENCompilerFlags`方法會套用至額外的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="60ba1-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="60ba1-113">`SetDesiredNGENCompilerFlags`方法必須呼叫期間[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="60ba1-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="60ba1-114">嘗試呼叫`SetDesiredNGENCompilerFlags`方法之後將會失敗。</span><span class="sxs-lookup"><span data-stu-id="60ba1-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="60ba1-115">嘗試設定不的旗標而且，定義於`CorDebugJITCompilerFlags`列舉型別或不合法的特定處理序將會失敗。</span><span class="sxs-lookup"><span data-stu-id="60ba1-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ba1-116">需求</span><span class="sxs-lookup"><span data-stu-id="60ba1-116">Requirements</span></span>  
 <span data-ttu-id="60ba1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60ba1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ba1-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60ba1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60ba1-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60ba1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60ba1-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ba1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ba1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60ba1-121">See also</span></span>

- [<span data-ttu-id="60ba1-122">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="60ba1-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="60ba1-123">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="60ba1-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
