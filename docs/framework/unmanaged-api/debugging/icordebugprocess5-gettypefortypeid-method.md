---
title: "ICorDebugProcess5::GetTypeForTypeID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeForTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4678575dba6210dc8c97f8ed18d5ded208a5c74e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="22ddb-102">ICorDebugProcess5::GetTypeForTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="22ddb-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="22ddb-103">將類型識別項轉換成 ICorDebugType 值。</span><span class="sxs-lookup"><span data-stu-id="22ddb-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ddb-104">語法</span><span class="sxs-lookup"><span data-stu-id="22ddb-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22ddb-105">參數</span><span class="sxs-lookup"><span data-stu-id="22ddb-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="22ddb-106">[in]類型識別項。</span><span class="sxs-lookup"><span data-stu-id="22ddb-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="22ddb-107">[out]ICorDebugType 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="22ddb-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22ddb-108">備註</span><span class="sxs-lookup"><span data-stu-id="22ddb-108">Remarks</span></span>  
 <span data-ttu-id="22ddb-109">在某些情況下，傳回型別識別項的方法會傳回 null`COR_TYPEID`值。</span><span class="sxs-lookup"><span data-stu-id="22ddb-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="22ddb-110">如果這個值會傳遞做為`id`引數，`GetTypeForTypeID`方法將會失敗，並傳回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="22ddb-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ddb-111">需求</span><span class="sxs-lookup"><span data-stu-id="22ddb-111">Requirements</span></span>  
 <span data-ttu-id="22ddb-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22ddb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22ddb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22ddb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22ddb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22ddb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22ddb-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22ddb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ddb-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="22ddb-116">See Also</span></span>  
 [<span data-ttu-id="22ddb-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="22ddb-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="22ddb-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="22ddb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
