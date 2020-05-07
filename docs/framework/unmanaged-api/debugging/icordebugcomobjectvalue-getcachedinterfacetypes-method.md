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
ms.openlocfilehash: 6b02657012870de4d0f888f6c05b115b25073fa2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892838"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="051ec-102">ICorDebugComObjectValue::GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="051ec-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="051ec-103">提供目前物件已轉換或當做使用之介面類別型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="051ec-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="051ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="051ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="051ec-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="051ec-106">在值，指出此方法是否只會傳回 Windows 執行階段介面（`IInspectable`介面）或由執行時間可呼叫包裝函式（RCW）所快取的所有 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="051ec-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="051ec-107">脫銷ICorDebugTypeEnum 列舉值之位址的指標，可提供 ICorDebugType 物件的存取，這些物件代表根據所篩選的快`bIInspectableOnly`取介面類別型。</span><span class="sxs-lookup"><span data-stu-id="051ec-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="051ec-108">備註</span><span class="sxs-lookup"><span data-stu-id="051ec-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051ec-109">需求</span><span class="sxs-lookup"><span data-stu-id="051ec-109">Requirements</span></span>  
 <span data-ttu-id="051ec-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="051ec-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="051ec-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="051ec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="051ec-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="051ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="051ec-113">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="051ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051ec-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="051ec-114">See also</span></span>

- [<span data-ttu-id="051ec-115">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="051ec-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="051ec-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="051ec-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
