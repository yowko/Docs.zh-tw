---
title: "ICorDebugManagedCallback::UnloadAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 731615729f680bae4c4b8517de4a3e522d4acae2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="68d8d-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="68d8d-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="68d8d-103">告知偵錯工具通用語言執行階段組件已卸載。</span><span class="sxs-lookup"><span data-stu-id="68d8d-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="68d8d-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="68d8d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="68d8d-106">[in]表示包含組件的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="68d8d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="68d8d-107">[in]代表組件 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="68d8d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68d8d-108">備註</span><span class="sxs-lookup"><span data-stu-id="68d8d-108">Remarks</span></span>  
 <span data-ttu-id="68d8d-109">組件不應該使用這個回呼之後。</span><span class="sxs-lookup"><span data-stu-id="68d8d-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d8d-110">需求</span><span class="sxs-lookup"><span data-stu-id="68d8d-110">Requirements</span></span>  
 <span data-ttu-id="68d8d-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68d8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d8d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68d8d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68d8d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68d8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68d8d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d8d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="68d8d-115">See Also</span></span>  
 [<span data-ttu-id="68d8d-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="68d8d-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="68d8d-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="68d8d-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
