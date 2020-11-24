---
title: ICorDebugManagedCallback::LoadModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 698a5cb88884febc4dfb3b916c00df20c1a77819
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679646"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="14f13-102">ICorDebugManagedCallback::LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="14f13-102">ICorDebugManagedCallback::LoadModule Method</span></span>

<span data-ttu-id="14f13-103">通知偵錯工具已順利載入 common language runtime (CLR) 模組。</span><span class="sxs-lookup"><span data-stu-id="14f13-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f13-104">語法</span><span class="sxs-lookup"><span data-stu-id="14f13-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14f13-105">參數</span><span class="sxs-lookup"><span data-stu-id="14f13-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="14f13-106">在ICorDebugAppDomain 物件的指標，代表已載入模組的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="14f13-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="14f13-107">在代表 CLR 模組之 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="14f13-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14f13-108">備註</span><span class="sxs-lookup"><span data-stu-id="14f13-108">Remarks</span></span>  

 <span data-ttu-id="14f13-109">`LoadModule`回呼提供適當的時間來檢查模組的中繼資料、設定及時 (JIT) 編譯器旗標，或啟用或停用模組的類別載入回呼。</span><span class="sxs-lookup"><span data-stu-id="14f13-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14f13-110">需求</span><span class="sxs-lookup"><span data-stu-id="14f13-110">Requirements</span></span>  

 <span data-ttu-id="14f13-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14f13-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f13-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14f13-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14f13-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14f13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14f13-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f13-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14f13-115">See also</span></span>

- [<span data-ttu-id="14f13-116">UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="14f13-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="14f13-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="14f13-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
