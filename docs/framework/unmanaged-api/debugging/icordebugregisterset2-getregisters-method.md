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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615185"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="79e8f-102">ICorDebugRegisterSet2：： GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="79e8f-102">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="79e8f-103">取得給定位元遮罩所指定之每個暫存器的值（適用于目前執行程式碼的平臺）。</span><span class="sxs-lookup"><span data-stu-id="79e8f-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="79e8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="79e8f-105">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="79e8f-106">在陣列的大小（以位元組為單位） `mask` 。</span><span class="sxs-lookup"><span data-stu-id="79e8f-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="79e8f-107">在位元組陣列，其中每個位對應至暫存器。</span><span class="sxs-lookup"><span data-stu-id="79e8f-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="79e8f-108">如果位為1，則會抓取對應的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="79e8f-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="79e8f-109">在要抓取的暫存器值數目。</span><span class="sxs-lookup"><span data-stu-id="79e8f-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="79e8f-110">脫銷物件的陣列 `CORDB_REGISTER` ，其中每一個都會接收暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="79e8f-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79e8f-111">備註</span><span class="sxs-lookup"><span data-stu-id="79e8f-111">Remarks</span></span>

 <span data-ttu-id="79e8f-112">`GetRegisters`方法會從遮罩所指定的暫存器中傳回值的陣列。</span><span class="sxs-lookup"><span data-stu-id="79e8f-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="79e8f-113">陣列不包含未設定其 mask 位的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="79e8f-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="79e8f-114">因此，陣列的大小 `regBuffer` 必須等於遮罩中的1。</span><span class="sxs-lookup"><span data-stu-id="79e8f-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="79e8f-115">如果的值 `regCount` 太小，用於遮罩所指示的暫存器數目，則較高編號的暫存器值將會從集合中截斷。</span><span class="sxs-lookup"><span data-stu-id="79e8f-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="79e8f-116">如果 `regCount` 太大，則不會修改未使用的 `regBuffer` 元素。</span><span class="sxs-lookup"><span data-stu-id="79e8f-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="79e8f-117">如果遮罩會指出無法使用的暫存器，則會傳回該暫存器的不定值。</span><span class="sxs-lookup"><span data-stu-id="79e8f-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="79e8f-118">在具有超過64暫存器的平臺中，此 `ICorDebugRegisterSet2::GetRegisters` 方法是必要的。</span><span class="sxs-lookup"><span data-stu-id="79e8f-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="79e8f-119">例如，IA64 具有128一般用途暫存器和128浮點暫存器，因此您在位元遮罩中需要超過64個位。</span><span class="sxs-lookup"><span data-stu-id="79e8f-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="79e8f-120">如果您沒有超過64暫存器（如 x86 之類的平臺）， `GetRegisters` 方法只會將位元組陣列中的位元組轉譯 `mask` 成 `ULONG64` ，然後呼叫[ICorDebugRegisterSet：： GetRegisters](icordebugregisterset-getregisters-method.md)方法，它會採用 `ULONG64` 遮罩。</span><span class="sxs-lookup"><span data-stu-id="79e8f-120">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e8f-121">需求</span><span class="sxs-lookup"><span data-stu-id="79e8f-121">Requirements</span></span>

 <span data-ttu-id="79e8f-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79e8f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e8f-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79e8f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79e8f-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79e8f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79e8f-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79e8f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e8f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e8f-126">See also</span></span>

- [<span data-ttu-id="79e8f-127">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="79e8f-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="79e8f-128">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="79e8f-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
