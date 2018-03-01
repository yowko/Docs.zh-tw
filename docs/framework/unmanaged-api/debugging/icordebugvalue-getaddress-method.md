---
title: "ICorDebugValue::GetAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8aa5a0c3740b6cf97d2a5d855343a36b90fd538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="5dafc-102">ICorDebugValue::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="5dafc-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="5dafc-103">取得正在進行偵錯這個 「 ICorDebugValue 」 物件的位址。</span><span class="sxs-lookup"><span data-stu-id="5dafc-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dafc-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dafc-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dafc-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dafc-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="5dafc-106">[out]指標`CORDB_ADDRESS`物件，指定這個值物件的位址。</span><span class="sxs-lookup"><span data-stu-id="5dafc-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dafc-107">備註</span><span class="sxs-lookup"><span data-stu-id="5dafc-107">Remarks</span></span>  
 <span data-ttu-id="5dafc-108">如果值為無法使用，則會傳回 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="5dafc-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="5dafc-109">這如果的值是在暫存器中至少一部分會發生問題，或是儲存在記憶體回收行程控制代碼 (`GCHandle`)。</span><span class="sxs-lookup"><span data-stu-id="5dafc-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dafc-110">需求</span><span class="sxs-lookup"><span data-stu-id="5dafc-110">Requirements</span></span>  
 <span data-ttu-id="5dafc-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dafc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dafc-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dafc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dafc-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dafc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dafc-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dafc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dafc-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dafc-115">See Also</span></span>  
 
