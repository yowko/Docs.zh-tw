---
title: ICorDebugValue::GetAddress 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b88c49ba93ff3c4cc3f5c7a656dfa5da6e82109e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559832"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="803cc-102">ICorDebugValue::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="803cc-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="803cc-103">取得正在進行偵錯這個 「 ICorDebugValue"物件的位址。</span><span class="sxs-lookup"><span data-stu-id="803cc-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="803cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="803cc-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="803cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="803cc-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="803cc-106">[out]指標`CORDB_ADDRESS`物件，指定此物件的位址值。</span><span class="sxs-lookup"><span data-stu-id="803cc-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="803cc-107">備註</span><span class="sxs-lookup"><span data-stu-id="803cc-107">Remarks</span></span>  
 <span data-ttu-id="803cc-108">如果值為無法使用，則會傳回 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="803cc-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="803cc-109">這可能發生的值是否在暫存器中，至少部分，或儲存在記憶體回收行程控制代碼 (`GCHandle`)。</span><span class="sxs-lookup"><span data-stu-id="803cc-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="803cc-110">需求</span><span class="sxs-lookup"><span data-stu-id="803cc-110">Requirements</span></span>  
 <span data-ttu-id="803cc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="803cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="803cc-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="803cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="803cc-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="803cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="803cc-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="803cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="803cc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="803cc-115">See also</span></span>

