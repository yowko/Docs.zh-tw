---
title: ICorDebugDataTarget::GetPlatform 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 5715f0634346dd0c6591cfe5687690aa0fba95f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125323"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="03071-102">ICorDebugDataTarget::GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="03071-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="03071-103">提供目標進程執行所在平臺的相關資訊，包括處理器架構和作業系統。</span><span class="sxs-lookup"><span data-stu-id="03071-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03071-104">語法</span><span class="sxs-lookup"><span data-stu-id="03071-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03071-105">參數</span><span class="sxs-lookup"><span data-stu-id="03071-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="03071-106">脫銷描述目標平臺之[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉的指標。</span><span class="sxs-lookup"><span data-stu-id="03071-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03071-107">備註</span><span class="sxs-lookup"><span data-stu-id="03071-107">Remarks</span></span>  
 <span data-ttu-id="03071-108">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面會使用 `CorDebugPlatformEnum` 列舉傳回值來判斷目標進程的詳細資料，例如其指標大小、位址空間配置、暫存器組、指令格式、內容配置和呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="03071-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="03071-109">`pTargetPlatform` 值可能會參考針對目標模擬的平臺，而不是指定實際使用的硬體。</span><span class="sxs-lookup"><span data-stu-id="03071-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="03071-110">例如，在 windows 作業系統64位版本的 windows on windows （WOW）環境中執行的進程，應使用[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉的 `CORDB_PLATFORM_WINDOWS_X86` 值。</span><span class="sxs-lookup"><span data-stu-id="03071-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="03071-111">這個方法必須成功。</span><span class="sxs-lookup"><span data-stu-id="03071-111">This method must succeed.</span></span> <span data-ttu-id="03071-112">如果失敗，則目標平臺無法使用。</span><span class="sxs-lookup"><span data-stu-id="03071-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="03071-113">方法可能會因為下列原因而失敗：</span><span class="sxs-lookup"><span data-stu-id="03071-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="03071-114">針對目標模擬的平臺無法使用。</span><span class="sxs-lookup"><span data-stu-id="03071-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="03071-115">目標平臺上的實際硬體無法使用。</span><span class="sxs-lookup"><span data-stu-id="03071-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03071-116">需求</span><span class="sxs-lookup"><span data-stu-id="03071-116">Requirements</span></span>  
 <span data-ttu-id="03071-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03071-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03071-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03071-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03071-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03071-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03071-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03071-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03071-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="03071-121">See also</span></span>

- [<span data-ttu-id="03071-122">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="03071-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="03071-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="03071-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="03071-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="03071-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
