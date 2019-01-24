---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d0d2c4af79a7d5a7123c5fe0ba043c2dd6302f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525803"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="4fa67-102">ICorDebugComObjectValue::GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="4fa67-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="4fa67-103">目前的物件已轉換成或做為介面類型提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="4fa67-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa67-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fa67-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fa67-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fa67-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="4fa67-106">[in]值，指出方法是否只傳回[!INCLUDE[wrt](../../../../includes/wrt-md.md)]介面 (`IInspectable`介面) 或快取執行階段可呼叫包裝函式 (RCW) 的所有 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="4fa67-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="4fa67-107">[out]ICorDebugTypeEnum 列舉程式，提供 ICorDebugType 物件，表示快取的介面類型的存取權的位址指標篩選根據`bIInspectableOnly`。</span><span class="sxs-lookup"><span data-stu-id="4fa67-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fa67-108">備註</span><span class="sxs-lookup"><span data-stu-id="4fa67-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa67-109">需求</span><span class="sxs-lookup"><span data-stu-id="4fa67-109">Requirements</span></span>  
 <span data-ttu-id="4fa67-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa67-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa67-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fa67-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fa67-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fa67-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fa67-113">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa67-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa67-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa67-114">See also</span></span>
- [<span data-ttu-id="4fa67-115">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="4fa67-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="4fa67-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4fa67-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
