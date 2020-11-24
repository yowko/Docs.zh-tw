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
ms.openlocfilehash: 6f1672d40cd495d3ec099abc703639cf52460703
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679659"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="458dc-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="458dc-102">ICorDebugManagedCallback::LoadClass Method</span></span>

<span data-ttu-id="458dc-103">通知偵錯工具已載入某個類別。</span><span class="sxs-lookup"><span data-stu-id="458dc-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="458dc-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="458dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="458dc-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="458dc-106">在ICorDebugAppDomain 物件的指標，代表已載入類別的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="458dc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="458dc-107">在代表類別之 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="458dc-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="458dc-108">備註</span><span class="sxs-lookup"><span data-stu-id="458dc-108">Remarks</span></span>  

 <span data-ttu-id="458dc-109">只有針對包含類別的模組啟用類別載入時，才會發生此回呼。</span><span class="sxs-lookup"><span data-stu-id="458dc-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="458dc-110">動態模組的類別載入一律會啟用。</span><span class="sxs-lookup"><span data-stu-id="458dc-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="458dc-111">`LoadClass`回呼提供適當的時間，可將中斷點系結至動態模組中新產生的類別。</span><span class="sxs-lookup"><span data-stu-id="458dc-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458dc-112">需求</span><span class="sxs-lookup"><span data-stu-id="458dc-112">Requirements</span></span>  

 <span data-ttu-id="458dc-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="458dc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458dc-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458dc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458dc-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458dc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458dc-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458dc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="458dc-117">See also</span></span>

- [<span data-ttu-id="458dc-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="458dc-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="458dc-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="458dc-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
