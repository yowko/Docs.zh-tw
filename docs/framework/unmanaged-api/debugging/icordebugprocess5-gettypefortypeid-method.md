---
title: ICorDebugProcess5::GetTypeForTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b5800890a5dfaef40225616f1d661a8e37ed4d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661096"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="48a7f-102">ICorDebugProcess5::GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="48a7f-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="48a7f-103">ICorDebugType 值會將型別識別項。</span><span class="sxs-lookup"><span data-stu-id="48a7f-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="48a7f-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48a7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="48a7f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="48a7f-106">[in]型別識別項。</span><span class="sxs-lookup"><span data-stu-id="48a7f-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="48a7f-107">[out]ICorDebugType 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="48a7f-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48a7f-108">備註</span><span class="sxs-lookup"><span data-stu-id="48a7f-108">Remarks</span></span>  
 <span data-ttu-id="48a7f-109">在某些情況下，傳回型別識別項的方法會傳回 null`COR_TYPEID`值。</span><span class="sxs-lookup"><span data-stu-id="48a7f-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="48a7f-110">如果此值被當做`id`引數`GetTypeForTypeID`方法將會失敗，並傳回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="48a7f-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a7f-111">需求</span><span class="sxs-lookup"><span data-stu-id="48a7f-111">Requirements</span></span>  
 <span data-ttu-id="48a7f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48a7f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48a7f-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48a7f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48a7f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48a7f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48a7f-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48a7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a7f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a7f-116">See also</span></span>
- [<span data-ttu-id="48a7f-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="48a7f-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="48a7f-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="48a7f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
