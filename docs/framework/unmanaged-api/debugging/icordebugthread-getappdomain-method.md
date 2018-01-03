---
title: "ICorDebugThread::GetAppDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c235bc0294b967e26766a095b85c5acf0f27cff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="2adfa-102">ICorDebugThread::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2adfa-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="2adfa-103">取得此 ICorDebugThread 目前執行所在的應用程式定義域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2adfa-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2adfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="2adfa-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2adfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="2adfa-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="2adfa-106">[out]表示這個執行緒目前執行所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="2adfa-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2adfa-107">需求</span><span class="sxs-lookup"><span data-stu-id="2adfa-107">Requirements</span></span>  
 <span data-ttu-id="2adfa-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2adfa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2adfa-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2adfa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2adfa-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2adfa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2adfa-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2adfa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
