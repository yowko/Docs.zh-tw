---
title: ICorDebugProcess5::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: ff2913399e1dbeb33bbfb697058db3caf2a8d1fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713102"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="b631c-102">ICorDebugProcess5::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="b631c-102">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="b631c-103">將物件位址轉換為 "ICorDebugObjectValue" 物件。</span><span class="sxs-lookup"><span data-stu-id="b631c-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b631c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b631c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b631c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b631c-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="b631c-106">在物件位址。</span><span class="sxs-lookup"><span data-stu-id="b631c-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="b631c-107">擴展"ICorDebugObjectValue" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="b631c-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b631c-108">備註</span><span class="sxs-lookup"><span data-stu-id="b631c-108">Remarks</span></span>  

 <span data-ttu-id="b631c-109">如果 `addr` 未指向有效的 managed 物件，則方法會傳回 `GetObject` `E_FAIL` 。</span><span class="sxs-lookup"><span data-stu-id="b631c-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b631c-110">需求</span><span class="sxs-lookup"><span data-stu-id="b631c-110">Requirements</span></span>  

 <span data-ttu-id="b631c-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b631c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b631c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b631c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b631c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b631c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b631c-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b631c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b631c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b631c-115">See also</span></span>

- [<span data-ttu-id="b631c-116">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="b631c-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="b631c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b631c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
