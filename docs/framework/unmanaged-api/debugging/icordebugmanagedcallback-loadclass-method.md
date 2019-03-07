---
title: ICorDebugManagedCallback::LoadClass 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8904f816f075b2c837f5c591ddb6697ba5a241f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478555"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="4fd94-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="4fd94-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="4fd94-103">已載入類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4fd94-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd94-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fd94-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd94-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fd94-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4fd94-106">[in]表示已載入類別所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="4fd94-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="4fd94-107">[in]ICorDebugClass 物件，代表的類別指標。</span><span class="sxs-lookup"><span data-stu-id="4fd94-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fd94-108">備註</span><span class="sxs-lookup"><span data-stu-id="4fd94-108">Remarks</span></span>  
 <span data-ttu-id="4fd94-109">只有當類別載入已啟用模組包含類別，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="4fd94-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="4fd94-110">類別載入一定會啟用動態模組。</span><span class="sxs-lookup"><span data-stu-id="4fd94-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="4fd94-111">`LoadClass`回呼會提供適當的時間，來將中斷點繫結至新產生的類別，在動態模組中。</span><span class="sxs-lookup"><span data-stu-id="4fd94-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd94-112">需求</span><span class="sxs-lookup"><span data-stu-id="4fd94-112">Requirements</span></span>  
 <span data-ttu-id="4fd94-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fd94-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd94-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fd94-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fd94-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fd94-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fd94-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd94-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fd94-117">See also</span></span>
- [<span data-ttu-id="4fd94-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="4fd94-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="4fd94-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4fd94-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
