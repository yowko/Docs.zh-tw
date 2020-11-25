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
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728364"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="d0333-102">ICorDebugValue::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="d0333-102">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="d0333-103">取得這個 "ICorDebugValue" 物件的位址，此物件正在進行正在進行調試的進程中。</span><span class="sxs-lookup"><span data-stu-id="d0333-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0333-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0333-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0333-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0333-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="d0333-106">擴展 `CORDB_ADDRESS` 物件的指標，該物件會指定這個值物件的位址。</span><span class="sxs-lookup"><span data-stu-id="d0333-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0333-107">備註</span><span class="sxs-lookup"><span data-stu-id="d0333-107">Remarks</span></span>  

 <span data-ttu-id="d0333-108">如果無法使用此值，則會傳回 0 (零) 。</span><span class="sxs-lookup"><span data-stu-id="d0333-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="d0333-109">如果值至少部分在暫存器中，或儲存在垃圾收集行程控制碼 () ，就可能發生這種情況 `GCHandle` 。</span><span class="sxs-lookup"><span data-stu-id="d0333-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0333-110">需求</span><span class="sxs-lookup"><span data-stu-id="d0333-110">Requirements</span></span>  

 <span data-ttu-id="d0333-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0333-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0333-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0333-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0333-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0333-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0333-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0333-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0333-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0333-115">See also</span></span>
