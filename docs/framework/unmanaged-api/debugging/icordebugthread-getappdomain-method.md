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
ms.openlocfilehash: a845eed993914e02de34ec5c60ed232ccabc561e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133520"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="8c046-102">ICorDebugThread::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="8c046-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="8c046-103">取得此 ICorDebugThread 目前執行所在之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="8c046-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c046-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c046-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c046-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c046-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="8c046-106">脫銷ICorDebugAppDomain 物件的指標，代表這個執行緒目前執行所在的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="8c046-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c046-107">需求</span><span class="sxs-lookup"><span data-stu-id="8c046-107">Requirements</span></span>  
 <span data-ttu-id="8c046-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c046-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c046-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c046-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c046-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c046-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c046-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c046-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
