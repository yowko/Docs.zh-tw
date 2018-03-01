---
title: "ICorDebugManagedCallback::LoadClass 方法"
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
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3e732b418398e9c917085d22507c9304981b06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="c255d-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="c255d-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="c255d-103">告知偵錯工具已載入類別。</span><span class="sxs-lookup"><span data-stu-id="c255d-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c255d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c255d-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c255d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c255d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c255d-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域到其中已載入類別指標。</span><span class="sxs-lookup"><span data-stu-id="c255d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="c255d-107">[in]表示類別 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c255d-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c255d-108">備註</span><span class="sxs-lookup"><span data-stu-id="c255d-108">Remarks</span></span>  
 <span data-ttu-id="c255d-109">只有當已啟用類別載入的模組包含的類別，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="c255d-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="c255d-110">類別載入一定會啟用動態模組。</span><span class="sxs-lookup"><span data-stu-id="c255d-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="c255d-111">`LoadClass`回呼會提供將中斷點繫結至新產生的類別，在動態模組中的適當時間。</span><span class="sxs-lookup"><span data-stu-id="c255d-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c255d-112">需求</span><span class="sxs-lookup"><span data-stu-id="c255d-112">Requirements</span></span>  
 <span data-ttu-id="c255d-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c255d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c255d-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c255d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c255d-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c255d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c255d-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c255d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c255d-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c255d-117">See Also</span></span>  
 [<span data-ttu-id="c255d-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="c255d-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="c255d-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c255d-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
