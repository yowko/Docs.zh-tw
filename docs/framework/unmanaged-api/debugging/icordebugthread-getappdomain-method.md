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
ms.openlocfilehash: 882176f381a7c5bc4a0297021b89a96948a1cea8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728065"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="25a73-102">ICorDebugThread::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="25a73-102">ICorDebugThread::GetAppDomain Method</span></span>

<span data-ttu-id="25a73-103">取得此 ICorDebugThread 目前執行所在之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="25a73-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a73-104">語法</span><span class="sxs-lookup"><span data-stu-id="25a73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25a73-105">參數</span><span class="sxs-lookup"><span data-stu-id="25a73-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="25a73-106">擴展ICorDebugAppDomain 物件的指標，代表這個執行緒目前執行所在的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="25a73-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a73-107">需求</span><span class="sxs-lookup"><span data-stu-id="25a73-107">Requirements</span></span>  

 <span data-ttu-id="25a73-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25a73-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a73-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25a73-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25a73-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25a73-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25a73-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25a73-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
