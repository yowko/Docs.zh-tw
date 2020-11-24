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
ms.openlocfilehash: f5f0f11683043f1c287dd3ca3071830bcfb46502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677553"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="d7994-102">ICorDebugComObjectValue::GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="d7994-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>

<span data-ttu-id="d7994-103">提供目前物件已轉換成或當做使用之介面類別型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d7994-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7994-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7994-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7994-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7994-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="d7994-106">在值，這個值會指出方法是否只傳回 Windows 執行階段介面 (介面) 或執行時間可呼叫包裝函式所快取 `IInspectable` 的所有 COM 介面 (RCW) 。</span><span class="sxs-lookup"><span data-stu-id="d7994-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="d7994-107">擴展ICorDebugTypeEnum 列舉值的位址指標，這個列舉值會提供 ICorDebugType 物件的存取權，這些物件代表根據所篩選的快取介面類別型 `bIInspectableOnly` 。</span><span class="sxs-lookup"><span data-stu-id="d7994-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7994-108">備註</span><span class="sxs-lookup"><span data-stu-id="d7994-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7994-109">需求</span><span class="sxs-lookup"><span data-stu-id="d7994-109">Requirements</span></span>  

 <span data-ttu-id="d7994-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7994-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7994-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7994-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7994-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7994-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7994-113">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7994-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7994-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7994-114">See also</span></span>

- [<span data-ttu-id="d7994-115">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="d7994-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d7994-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d7994-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
