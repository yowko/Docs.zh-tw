---
title: ICorDebugRegisterSet2::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136691"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="cb78b-102">ICorDebugRegisterSet2::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="cb78b-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="cb78b-103">取得每個暫存器值 （適用於目前執行所在的程式碼的平台） 所指定的特定位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="cb78b-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb78b-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb78b-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb78b-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb78b-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="cb78b-106">[in]大小，以位元組為單位的`mask`陣列。</span><span class="sxs-lookup"><span data-stu-id="cb78b-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="cb78b-107">[in]位元組陣列，其中每個位元對應暫存器。</span><span class="sxs-lookup"><span data-stu-id="cb78b-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="cb78b-108">如果位元為 1，將會擷取對應的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="cb78b-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="cb78b-109">[in]要擷取的暫存器值數目。</span><span class="sxs-lookup"><span data-stu-id="cb78b-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="cb78b-110">[out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="cb78b-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb78b-111">備註</span><span class="sxs-lookup"><span data-stu-id="cb78b-111">Remarks</span></span>  
 <span data-ttu-id="cb78b-112">`GetRegisters`方法會從遮罩所指定的暫存器傳回值的陣列。</span><span class="sxs-lookup"><span data-stu-id="cb78b-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="cb78b-113">陣列未包含暫存器未設定位元的遮罩的值。</span><span class="sxs-lookup"><span data-stu-id="cb78b-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="cb78b-114">因此，大小`regBuffer`必須等於遮罩中數字 1 的陣列。</span><span class="sxs-lookup"><span data-stu-id="cb78b-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="cb78b-115">如果值`regCount`為太小會從集合中截斷的遮罩，較高編號的暫存器的值所表示的暫存器數目。</span><span class="sxs-lookup"><span data-stu-id="cb78b-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="cb78b-116">如果`regCount`太大，未使用`regBuffer`項目將會是未修改。</span><span class="sxs-lookup"><span data-stu-id="cb78b-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="cb78b-117">如果無法使用的暫存器由遮罩，就會傳回不定值的一個該暫存器。</span><span class="sxs-lookup"><span data-stu-id="cb78b-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="cb78b-118">`ICorDebugRegisterSet2::GetRegisters`方法是必要的平台具有 64 個以上的暫存器。</span><span class="sxs-lookup"><span data-stu-id="cb78b-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="cb78b-119">比方說，IA64 有 128 一般用途的暫存器和 128 的浮點數暫存器，因此您需要更大 64 位元的位元遮罩中。</span><span class="sxs-lookup"><span data-stu-id="cb78b-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="cb78b-120">如果您不需要 64 個以上的暫存器，在此情況下，例如 x86 平台上的`GetRegisters`方法實際上只會轉譯中的位元組`mask`位元組陣列`ULONG64`，然後呼叫[ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)方法，後者會採用`ULONG64`遮罩。</span><span class="sxs-lookup"><span data-stu-id="cb78b-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb78b-121">需求</span><span class="sxs-lookup"><span data-stu-id="cb78b-121">Requirements</span></span>  
 <span data-ttu-id="cb78b-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb78b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb78b-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb78b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb78b-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb78b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb78b-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb78b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb78b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb78b-126">See also</span></span>

- [<span data-ttu-id="cb78b-127">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="cb78b-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="cb78b-128">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="cb78b-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
