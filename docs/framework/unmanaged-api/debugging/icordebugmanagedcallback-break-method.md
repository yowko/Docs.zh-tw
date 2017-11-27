---
title: "ICorDebugManagedCallback::Break 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Break
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce51ed25ecd5570ce3c5d9acc1ec3750b289f095
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="835fb-102">ICorDebugManagedCallback::Break 方法</span><span class="sxs-lookup"><span data-stu-id="835fb-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="835fb-103">告知偵錯工具時<xref:System.Reflection.Emit.OpCodes.Break>執行指令碼資料流中的。</span><span class="sxs-lookup"><span data-stu-id="835fb-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="835fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="835fb-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="835fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="835fb-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="835fb-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含 break 指令指標。</span><span class="sxs-lookup"><span data-stu-id="835fb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="835fb-107">[in]表示包含 break 指令的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="835fb-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="835fb-108">需求</span><span class="sxs-lookup"><span data-stu-id="835fb-108">Requirements</span></span>  
 <span data-ttu-id="835fb-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="835fb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="835fb-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="835fb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="835fb-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="835fb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="835fb-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="835fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835fb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="835fb-113">See Also</span></span>  
 [<span data-ttu-id="835fb-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="835fb-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
