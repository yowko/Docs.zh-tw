---
title: "ICorDebugManagedCallback::UnloadAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29400e5bda2a17c731cb33e67c0123cffc89c48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="5239e-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5239e-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="5239e-103">告知偵錯工具通用語言執行階段組件已卸載。</span><span class="sxs-lookup"><span data-stu-id="5239e-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5239e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5239e-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5239e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5239e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5239e-106">[in]表示包含組件的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="5239e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="5239e-107">[in]代表組件 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="5239e-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5239e-108">備註</span><span class="sxs-lookup"><span data-stu-id="5239e-108">Remarks</span></span>  
 <span data-ttu-id="5239e-109">組件不應該使用這個回呼之後。</span><span class="sxs-lookup"><span data-stu-id="5239e-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5239e-110">需求</span><span class="sxs-lookup"><span data-stu-id="5239e-110">Requirements</span></span>  
 <span data-ttu-id="5239e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5239e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5239e-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5239e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5239e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5239e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5239e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5239e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5239e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5239e-115">See Also</span></span>  
 [<span data-ttu-id="5239e-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5239e-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="5239e-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5239e-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
