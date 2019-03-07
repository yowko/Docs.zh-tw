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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4cdaf87b6fd65eecbe62f2e3b927eee6094e72
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496166"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="63ee7-102">ICorDebugDataTarget::GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="63ee7-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="63ee7-103">提供的平台，包括處理器架構與目標處理序執行所在的作業系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63ee7-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63ee7-104">語法</span><span class="sxs-lookup"><span data-stu-id="63ee7-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63ee7-105">參數</span><span class="sxs-lookup"><span data-stu-id="63ee7-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="63ee7-106">[out]指標[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉型別描述的目標平台。</span><span class="sxs-lookup"><span data-stu-id="63ee7-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63ee7-107">備註</span><span class="sxs-lookup"><span data-stu-id="63ee7-107">Remarks</span></span>  
 <span data-ttu-id="63ee7-108">`CorDebugPlatformEnum`列舉型別傳回值由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面，以判斷目標處理序，例如其指標大小、 位址空間配置、 暫存器組合、 指示格式、 內容配置的詳細資料和呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="63ee7-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="63ee7-109">`pTargetPlatform`值可能會參考正在模擬的目標，而不是使用中指定實際的硬體平台。</span><span class="sxs-lookup"><span data-stu-id="63ee7-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="63ee7-110">例如，使用 64 位元版本的 Windows 作業系統執行 Windows (WOW) 環境上的 Windows 中的程序應該`CORDB_PLATFORM_WINDOWS_X86`的值[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="63ee7-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="63ee7-111">這個方法必須成功。</span><span class="sxs-lookup"><span data-stu-id="63ee7-111">This method must succeed.</span></span> <span data-ttu-id="63ee7-112">如果失敗，目標平台是無法使用。</span><span class="sxs-lookup"><span data-stu-id="63ee7-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="63ee7-113">此方法可能會失敗，原因如下：</span><span class="sxs-lookup"><span data-stu-id="63ee7-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="63ee7-114">正在模擬的目標平台是無法使用。</span><span class="sxs-lookup"><span data-stu-id="63ee7-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="63ee7-115">目標平台上實際的硬體就無法使用。</span><span class="sxs-lookup"><span data-stu-id="63ee7-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63ee7-116">需求</span><span class="sxs-lookup"><span data-stu-id="63ee7-116">Requirements</span></span>  
 <span data-ttu-id="63ee7-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63ee7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63ee7-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63ee7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63ee7-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63ee7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63ee7-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63ee7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ee7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ee7-121">See also</span></span>
- [<span data-ttu-id="63ee7-122">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="63ee7-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="63ee7-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="63ee7-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="63ee7-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="63ee7-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
