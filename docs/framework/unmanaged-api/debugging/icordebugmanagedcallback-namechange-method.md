---
title: "ICorDebugManagedCallback::NameChange 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.NameChange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9ce32a68354c6bef43dfb55395cb6f9bb136dca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="0222f-102">ICorDebugManagedCallback::NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="0222f-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="0222f-103">告知偵錯工具應用程式定義域或執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="0222f-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0222f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0222f-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0222f-105">參數</span><span class="sxs-lookup"><span data-stu-id="0222f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0222f-106">[in]ICorDebugAppDomain 物件，表示可能發生的名稱變更，應用程式定義域的指標包含在名稱變更的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0222f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0222f-107">[in]ICorDebugThread 物件，表示執行緒名稱變更的指標。</span><span class="sxs-lookup"><span data-stu-id="0222f-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0222f-108">需求</span><span class="sxs-lookup"><span data-stu-id="0222f-108">Requirements</span></span>  
 <span data-ttu-id="0222f-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0222f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0222f-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0222f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0222f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0222f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0222f-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0222f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0222f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0222f-113">See Also</span></span>  
 [<span data-ttu-id="0222f-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0222f-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
