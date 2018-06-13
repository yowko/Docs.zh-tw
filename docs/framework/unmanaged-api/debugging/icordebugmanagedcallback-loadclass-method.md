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
ms.openlocfilehash: f1d920a97338bba3e90ec8f0c440f6dd2a93e722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416201"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="589de-102">ICorDebugManagedCallback::LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="589de-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="589de-103">告知偵錯工具已載入類別。</span><span class="sxs-lookup"><span data-stu-id="589de-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="589de-104">語法</span><span class="sxs-lookup"><span data-stu-id="589de-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="589de-105">參數</span><span class="sxs-lookup"><span data-stu-id="589de-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="589de-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域到其中已載入類別指標。</span><span class="sxs-lookup"><span data-stu-id="589de-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="589de-107">[in]表示類別 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="589de-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="589de-108">備註</span><span class="sxs-lookup"><span data-stu-id="589de-108">Remarks</span></span>  
 <span data-ttu-id="589de-109">只有當已啟用類別載入的模組包含的類別，就會發生這個回呼。</span><span class="sxs-lookup"><span data-stu-id="589de-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="589de-110">類別載入一定會啟用動態模組。</span><span class="sxs-lookup"><span data-stu-id="589de-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="589de-111">`LoadClass`回呼會提供將中斷點繫結至新產生的類別，在動態模組中的適當時間。</span><span class="sxs-lookup"><span data-stu-id="589de-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="589de-112">需求</span><span class="sxs-lookup"><span data-stu-id="589de-112">Requirements</span></span>  
 <span data-ttu-id="589de-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="589de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="589de-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="589de-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="589de-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="589de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="589de-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="589de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589de-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="589de-117">See Also</span></span>  
 [<span data-ttu-id="589de-118">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="589de-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="589de-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="589de-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
