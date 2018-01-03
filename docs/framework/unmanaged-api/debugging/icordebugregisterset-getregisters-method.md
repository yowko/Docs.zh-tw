---
title: "ICorDebugRegisterSet::GetRegisters 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="816a6-102">ICorDebugRegisterSet::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="816a6-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="816a6-103">取得每個暫存器值 （在電腦上目前正在執行的程式碼） 的位元遮罩所指定。</span><span class="sxs-lookup"><span data-stu-id="816a6-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="816a6-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="816a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="816a6-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="816a6-106">[in]位元遮罩，指定的值為要擷取哪一個暫存器。</span><span class="sxs-lookup"><span data-stu-id="816a6-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="816a6-107">每個位元對應暫存器。</span><span class="sxs-lookup"><span data-stu-id="816a6-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="816a6-108">如果一個位元設定為其中一個，擷取暫存器的值;否則，不會擷取暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="816a6-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="816a6-109">[in]要擷取的暫存器值數目。</span><span class="sxs-lookup"><span data-stu-id="816a6-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="816a6-110">[out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="816a6-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="816a6-111">備註</span><span class="sxs-lookup"><span data-stu-id="816a6-111">Remarks</span></span>  
 <span data-ttu-id="816a6-112">陣列的大小應該會等於設為其中一個位元遮罩中的位元數。</span><span class="sxs-lookup"><span data-stu-id="816a6-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="816a6-113">`regCount`參數緩衝區將會接收暫存器值中指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="816a6-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="816a6-114">如果`regCount`值是由遮罩所指示的暫存器數目太小，較高編號的暫存器會從集合中截斷。</span><span class="sxs-lookup"><span data-stu-id="816a6-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="816a6-115">如果`regCount`值太大，而未使用`regBuffer`項目就是未修改。</span><span class="sxs-lookup"><span data-stu-id="816a6-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="816a6-116">如果位元遮罩指定的暫存器無法使用，`GetRegisters`傳回該暫存器的不定值。</span><span class="sxs-lookup"><span data-stu-id="816a6-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="816a6-117">需求</span><span class="sxs-lookup"><span data-stu-id="816a6-117">Requirements</span></span>  
 <span data-ttu-id="816a6-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="816a6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816a6-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="816a6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="816a6-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="816a6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="816a6-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816a6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816a6-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="816a6-122">See Also</span></span>  
 [<span data-ttu-id="816a6-123">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="816a6-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="816a6-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="816a6-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
