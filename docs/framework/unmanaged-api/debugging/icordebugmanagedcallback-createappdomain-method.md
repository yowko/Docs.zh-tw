---
title: ICorDebugManagedCallback::CreateAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f831f0f42231f594e170567535af75216e68c45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721305"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="6b5bd-102">ICorDebugManagedCallback::CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="6b5bd-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>

<span data-ttu-id="6b5bd-103">通知偵錯工具已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b5bd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b5bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b5bd-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="6b5bd-106">在ICorDebugProcess 物件的指標，該物件表示建立應用程式網域的進程。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="6b5bd-107">在ICorDebugAppDomain 物件的指標，代表已建立的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b5bd-108">需求</span><span class="sxs-lookup"><span data-stu-id="6b5bd-108">Requirements</span></span>  

 <span data-ttu-id="6b5bd-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b5bd-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b5bd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b5bd-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b5bd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b5bd-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b5bd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5bd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b5bd-113">See also</span></span>

- [<span data-ttu-id="6b5bd-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6b5bd-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
