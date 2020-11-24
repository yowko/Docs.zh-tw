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
ms.openlocfilehash: 40b944f6a1204bfe506ed64408be30f68adf3170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675252"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="ca13b-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="ca13b-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="ca13b-103">設定必須內嵌在先行編譯映射中的旗標，以便執行時間將該影像載入至目前的進程。</span><span class="sxs-lookup"><span data-stu-id="ca13b-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca13b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca13b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca13b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca13b-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="ca13b-106">在 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉的值，指定用來選取正確預先編譯影像的編譯器旗標。</span><span class="sxs-lookup"><span data-stu-id="ca13b-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca13b-107">備註</span><span class="sxs-lookup"><span data-stu-id="ca13b-107">Remarks</span></span>  

 <span data-ttu-id="ca13b-108">`SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯映射中的旗標，以便執行時間將該影像載入至此進程。</span><span class="sxs-lookup"><span data-stu-id="ca13b-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="ca13b-109">這個方法所設定的旗標只會用來選取正確的預先編譯映射。</span><span class="sxs-lookup"><span data-stu-id="ca13b-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="ca13b-110">如果沒有這類影像，則執行時間會改為載入 Microsoft 中繼語言 (MSIL) 映射以及即時 (JIT) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="ca13b-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="ca13b-111">在這種情況下，偵錯工具仍然必須使用 [ICorDebugModule2：： SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) 方法來設定 JIT 編譯所需的旗標。</span><span class="sxs-lookup"><span data-stu-id="ca13b-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="ca13b-112">如果載入影像，但必須針對該映射進行某些 JIT 編譯 (如果映射包含泛型) ，則方法所指定的編譯器旗標 `SetDesiredNGENCompilerFlags` 將會套用到額外的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="ca13b-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="ca13b-113">您 `SetDesiredNGENCompilerFlags` 必須在 [ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md) 回呼中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ca13b-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="ca13b-114">之後嘗試呼叫 `SetDesiredNGENCompilerFlags` 方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ca13b-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="ca13b-115">此外，嘗試設定列舉中未定義 `CorDebugJITCompilerFlags` 或對指定進程而言不合法的旗標將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ca13b-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca13b-116">需求</span><span class="sxs-lookup"><span data-stu-id="ca13b-116">Requirements</span></span>  

 <span data-ttu-id="ca13b-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca13b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca13b-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca13b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca13b-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca13b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca13b-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca13b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca13b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca13b-121">See also</span></span>

- [<span data-ttu-id="ca13b-122">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="ca13b-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="ca13b-123">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ca13b-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
