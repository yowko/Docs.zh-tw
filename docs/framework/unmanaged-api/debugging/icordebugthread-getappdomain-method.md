---
title: ICorDebugThread::GetAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a37ee8367006975b0f8ee4fa638ae3d72f9486
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487742"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="85b70-102">ICorDebugThread::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="85b70-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="85b70-103">取得此 ICorDebugThread 目前執行所在的應用程式定義域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="85b70-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b70-104">語法</span><span class="sxs-lookup"><span data-stu-id="85b70-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85b70-105">參數</span><span class="sxs-lookup"><span data-stu-id="85b70-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="85b70-106">[out]表示這個執行緒目前執行所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="85b70-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b70-107">需求</span><span class="sxs-lookup"><span data-stu-id="85b70-107">Requirements</span></span>  
 <span data-ttu-id="85b70-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85b70-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b70-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85b70-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85b70-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85b70-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85b70-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b70-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
