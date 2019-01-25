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
ms.openlocfilehash: 354de38e106ea16eef10bd9a9cebf2b27ca44d25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548124"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="d23ae-102">ICorDebugManagedCallback::UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="d23ae-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="d23ae-103">正在卸載類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d23ae-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="d23ae-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="d23ae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d23ae-106">[in]表示包含類別的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="d23ae-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="d23ae-107">[in]ICorDebugClass 物件，代表的類別指標。</span><span class="sxs-lookup"><span data-stu-id="d23ae-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23ae-108">備註</span><span class="sxs-lookup"><span data-stu-id="d23ae-108">Remarks</span></span>  
 <span data-ttu-id="d23ae-109">在這個呼叫之後，類別不應參考。</span><span class="sxs-lookup"><span data-stu-id="d23ae-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23ae-110">需求</span><span class="sxs-lookup"><span data-stu-id="d23ae-110">Requirements</span></span>  
 <span data-ttu-id="d23ae-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d23ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23ae-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d23ae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d23ae-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d23ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d23ae-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23ae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d23ae-115">See also</span></span>
- [<span data-ttu-id="d23ae-116">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="d23ae-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="d23ae-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d23ae-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
