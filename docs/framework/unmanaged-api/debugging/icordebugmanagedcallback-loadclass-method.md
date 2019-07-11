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
ms.openlocfilehash: 5619dea17b9a7140238fd559d2f6b1a5d190ac33
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761892"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="9868f-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="9868f-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="9868f-103">已載入類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="9868f-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9868f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9868f-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9868f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9868f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9868f-106">[in]表示已載入類別所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="9868f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="9868f-107">[in]ICorDebugClass 物件，代表的類別指標。</span><span class="sxs-lookup"><span data-stu-id="9868f-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9868f-108">備註</span><span class="sxs-lookup"><span data-stu-id="9868f-108">Remarks</span></span>  
 <span data-ttu-id="9868f-109">只有當類別載入已啟用模組包含類別，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="9868f-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="9868f-110">類別載入一定會啟用動態模組。</span><span class="sxs-lookup"><span data-stu-id="9868f-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="9868f-111">`LoadClass`回呼會提供適當的時間，來將中斷點繫結至新產生的類別，在動態模組中。</span><span class="sxs-lookup"><span data-stu-id="9868f-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9868f-112">需求</span><span class="sxs-lookup"><span data-stu-id="9868f-112">Requirements</span></span>  
 <span data-ttu-id="9868f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9868f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9868f-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9868f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9868f-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9868f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9868f-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9868f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9868f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9868f-117">See also</span></span>

- [<span data-ttu-id="9868f-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="9868f-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="9868f-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9868f-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
