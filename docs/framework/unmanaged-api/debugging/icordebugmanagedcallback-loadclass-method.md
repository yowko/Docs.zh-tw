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
ms.openlocfilehash: cc5a2e1de79d6ba04ff3bf2bf86e0cb7ce9a5c0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788382"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="f0ac8-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="f0ac8-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="f0ac8-103">通知偵錯工具已載入類別。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ac8-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0ac8-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ac8-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0ac8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f0ac8-106">在ICorDebugAppDomain 物件的指標，表示已載入類別的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="f0ac8-107">在表示類別之 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0ac8-108">備註</span><span class="sxs-lookup"><span data-stu-id="f0ac8-108">Remarks</span></span>  
 <span data-ttu-id="f0ac8-109">只有在已針對包含類別的模組啟用類別載入時，才會發生此回呼。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="f0ac8-110">動態模組的類別載入一律為啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="f0ac8-111">`LoadClass` 回呼會提供適當的時間，將中斷點系結至動態模組中新產生的類別。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ac8-112">需求</span><span class="sxs-lookup"><span data-stu-id="f0ac8-112">Requirements</span></span>  
 <span data-ttu-id="f0ac8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ac8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ac8-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0ac8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0ac8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0ac8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0ac8-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ac8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ac8-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ac8-117">See also</span></span>

- [<span data-ttu-id="f0ac8-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="f0ac8-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="f0ac8-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f0ac8-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
