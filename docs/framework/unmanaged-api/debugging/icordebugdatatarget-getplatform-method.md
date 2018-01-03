---
title: "ICorDebugDataTarget::GetPlatform 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetPlatform Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c19e472ef571def1011d2a00701fea3a6fadfea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="78efa-102">ICorDebugDataTarget::GetPlatform 方法</span><span class="sxs-lookup"><span data-stu-id="78efa-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="78efa-103">提供的平台，包括處理器架構與目標處理序執行所在的作業系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="78efa-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78efa-104">語法</span><span class="sxs-lookup"><span data-stu-id="78efa-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78efa-105">參數</span><span class="sxs-lookup"><span data-stu-id="78efa-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="78efa-106">[out]指標[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉，其描述的目標平台。</span><span class="sxs-lookup"><span data-stu-id="78efa-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78efa-107">備註</span><span class="sxs-lookup"><span data-stu-id="78efa-107">Remarks</span></span>  
 <span data-ttu-id="78efa-108">`CorDebugPlatformEnum`列舉傳回值由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面，以判斷目標處理序，例如指標大小、 位址空間配置、 登錄設定、 指示格式、 內容配置的詳細資料，呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="78efa-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="78efa-109">`pTargetPlatform`值可能會參考正在模擬的目標，而非使用中指定實際的硬體平台。</span><span class="sxs-lookup"><span data-stu-id="78efa-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="78efa-110">例如，在 64 位元版本 Windows 作業系統的 Windows on Windows (WOW) 環境中執行的處理序應該使用`CORDB_PLATFORM_WINDOWS_X86`值[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="78efa-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="78efa-111">這個方法必須成功。</span><span class="sxs-lookup"><span data-stu-id="78efa-111">This method must succeed.</span></span> <span data-ttu-id="78efa-112">如果失敗，則目標平台是無法使用。</span><span class="sxs-lookup"><span data-stu-id="78efa-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="78efa-113">此方法可能會失敗，原因如下：</span><span class="sxs-lookup"><span data-stu-id="78efa-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="78efa-114">目標正在模擬的平台是無法使用。</span><span class="sxs-lookup"><span data-stu-id="78efa-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="78efa-115">目標平台上的實際硬體便無法使用。</span><span class="sxs-lookup"><span data-stu-id="78efa-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78efa-116">需求</span><span class="sxs-lookup"><span data-stu-id="78efa-116">Requirements</span></span>  
 <span data-ttu-id="78efa-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78efa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78efa-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78efa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78efa-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78efa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78efa-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78efa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78efa-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="78efa-121">See Also</span></span>  
 [<span data-ttu-id="78efa-122">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="78efa-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="78efa-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="78efa-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="78efa-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="78efa-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
