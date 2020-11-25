---
title: ICorDebugManagedCallback::NameChange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 0307ad5794d641833c2da1a1674e455ebff24861
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726518"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="c495a-102">ICorDebugManagedCallback::NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="c495a-102">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="c495a-103">通知偵錯工具，其中應用程式域或執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="c495a-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c495a-104">語法</span><span class="sxs-lookup"><span data-stu-id="c495a-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c495a-105">參數</span><span class="sxs-lookup"><span data-stu-id="c495a-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="c495a-106">在ICorDebugAppDomain 物件的指標，代表名稱變更或包含名稱變更之執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="c495a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c495a-107">在代表名稱變更之執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="c495a-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c495a-108">需求</span><span class="sxs-lookup"><span data-stu-id="c495a-108">Requirements</span></span>  

 <span data-ttu-id="c495a-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c495a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c495a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c495a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c495a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c495a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c495a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c495a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c495a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c495a-113">See also</span></span>

- [<span data-ttu-id="c495a-114">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c495a-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
