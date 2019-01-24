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
ms.openlocfilehash: bc0dde4f2455ed45ddf8ca1efefa7ab67ba04f6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660771"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="104e4-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="104e4-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="104e4-103">設定必須內嵌在先行編譯的映像，以便將該映像載入目前的程序的執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="104e4-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="104e4-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="104e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="104e4-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="104e4-106">[in]值為[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定的編譯器旗標用來選取正確的先行編譯映像。</span><span class="sxs-lookup"><span data-stu-id="104e4-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="104e4-107">備註</span><span class="sxs-lookup"><span data-stu-id="104e4-107">Remarks</span></span>  
 <span data-ttu-id="104e4-108">`SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯的映像中，以便在執行階段會載入此程序的該映像的旗標。</span><span class="sxs-lookup"><span data-stu-id="104e4-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="104e4-109">這個方法所設定的旗標是只能用來選取正確的先行編譯映像。</span><span class="sxs-lookup"><span data-stu-id="104e4-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="104e4-110">如果沒有這類映像存在時，執行階段將 Microsoft intermediate language (MSIL) 映像，而且在 just-in-time (JIT) 編譯器改為載入。</span><span class="sxs-lookup"><span data-stu-id="104e4-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="104e4-111">在此情況下，仍然必須使用偵錯工具[ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法，以進行 JIT 編譯，視需要設定之旗標。</span><span class="sxs-lookup"><span data-stu-id="104e4-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="104e4-112">如果已載入的映像，但一些 JIT 編譯必須進行該映像 （這會是大小寫，如果映像包含泛型），所指定的編譯器旗標`SetDesiredNGENCompilerFlags`方法會套用至額外的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="104e4-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="104e4-113">`SetDesiredNGENCompilerFlags`方法必須呼叫期間[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="104e4-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="104e4-114">嘗試呼叫`SetDesiredNGENCompilerFlags`方法之後將會失敗。</span><span class="sxs-lookup"><span data-stu-id="104e4-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="104e4-115">嘗試設定不的旗標而且，定義於`CorDebugJITCompilerFlags`列舉型別或不合法的特定處理序將會失敗。</span><span class="sxs-lookup"><span data-stu-id="104e4-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="104e4-116">需求</span><span class="sxs-lookup"><span data-stu-id="104e4-116">Requirements</span></span>  
 <span data-ttu-id="104e4-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="104e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="104e4-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="104e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="104e4-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="104e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="104e4-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="104e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104e4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="104e4-121">See also</span></span>
- [<span data-ttu-id="104e4-122">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="104e4-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="104e4-123">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="104e4-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
