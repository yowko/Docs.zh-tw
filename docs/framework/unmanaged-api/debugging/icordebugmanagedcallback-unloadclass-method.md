---
title: ICorDebugManagedCallback::UnloadClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3eb8bf59ee2a91c62a6ff74b1903d92607a9ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197855"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="868f4-102">ICorDebugManagedCallback::UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="868f4-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="868f4-103">正在卸載類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="868f4-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="868f4-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="868f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="868f4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="868f4-106">[in]表示包含類別的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="868f4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="868f4-107">[in]ICorDebugClass 物件，代表的類別指標。</span><span class="sxs-lookup"><span data-stu-id="868f4-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="868f4-108">備註</span><span class="sxs-lookup"><span data-stu-id="868f4-108">Remarks</span></span>  
 <span data-ttu-id="868f4-109">在這個呼叫之後，類別不應參考。</span><span class="sxs-lookup"><span data-stu-id="868f4-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="868f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="868f4-110">Requirements</span></span>  
 <span data-ttu-id="868f4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="868f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="868f4-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="868f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="868f4-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="868f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="868f4-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="868f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868f4-115">See also</span></span>

- [<span data-ttu-id="868f4-116">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="868f4-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="868f4-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="868f4-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
