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
ms.openlocfilehash: f2f19987d22502acbe06bd5e5c14b0d6c17cbe24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781576"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="31013-102">ICorDebugManagedCallback::UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="31013-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="31013-103">通知偵錯工具正在卸載類別。</span><span class="sxs-lookup"><span data-stu-id="31013-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31013-104">語法</span><span class="sxs-lookup"><span data-stu-id="31013-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31013-105">參數</span><span class="sxs-lookup"><span data-stu-id="31013-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="31013-106">在ICorDebugAppDomain 物件的指標，表示包含類別的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="31013-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="31013-107">在表示類別之 ICorDebugClass 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="31013-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31013-108">備註</span><span class="sxs-lookup"><span data-stu-id="31013-108">Remarks</span></span>  
 <span data-ttu-id="31013-109">在此呼叫之後，不應參考類別。</span><span class="sxs-lookup"><span data-stu-id="31013-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31013-110">需求</span><span class="sxs-lookup"><span data-stu-id="31013-110">Requirements</span></span>  
 <span data-ttu-id="31013-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31013-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31013-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31013-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31013-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31013-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31013-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31013-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31013-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="31013-115">See also</span></span>

- [<span data-ttu-id="31013-116">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="31013-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="31013-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="31013-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
