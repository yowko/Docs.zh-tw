---
title: ICorDebugRegisterSet::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178537"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="fef8a-102">ICorDebugRegisterSet::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="fef8a-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="fef8a-103">獲取位元遮罩指定的每個寄存器的值（當前正在執行代碼的電腦）。</span><span class="sxs-lookup"><span data-stu-id="fef8a-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fef8a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fef8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="fef8a-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="fef8a-106">[在]指定要檢索哪些寄存器值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="fef8a-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="fef8a-107">每個位對應于寄存器。</span><span class="sxs-lookup"><span data-stu-id="fef8a-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="fef8a-108">如果位設置為 1，則檢索寄存器的值;如果位設置為 1，則檢索寄存器的值。否則，不會檢索寄存器的值。</span><span class="sxs-lookup"><span data-stu-id="fef8a-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="fef8a-109">[在]要檢索的寄存器值數。</span><span class="sxs-lookup"><span data-stu-id="fef8a-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="fef8a-110">[出]物件陣列`CORDB_REGISTER`，每個物件都接收寄存器的值。</span><span class="sxs-lookup"><span data-stu-id="fef8a-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fef8a-111">備註</span><span class="sxs-lookup"><span data-stu-id="fef8a-111">Remarks</span></span>  
 <span data-ttu-id="fef8a-112">陣列的大小應等於位元遮罩中設置為 1 的位數。</span><span class="sxs-lookup"><span data-stu-id="fef8a-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="fef8a-113">參數`regCount`指定將接收寄存器值的緩衝區中的元素數。</span><span class="sxs-lookup"><span data-stu-id="fef8a-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="fef8a-114">如果`regCount`該值對於遮罩指示的寄存器數太小，則較高的編號寄存器將從集中截斷。</span><span class="sxs-lookup"><span data-stu-id="fef8a-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="fef8a-115">如果`regCount`該值太大，則未使用`regBuffer`的元素將取消修改。</span><span class="sxs-lookup"><span data-stu-id="fef8a-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="fef8a-116">如果位元遮罩指定不可用的寄存器，`GetRegisters`則返回該寄存器的不確定值。</span><span class="sxs-lookup"><span data-stu-id="fef8a-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef8a-117">需求</span><span class="sxs-lookup"><span data-stu-id="fef8a-117">Requirements</span></span>  
 <span data-ttu-id="fef8a-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fef8a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef8a-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fef8a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fef8a-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fef8a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fef8a-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef8a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef8a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fef8a-122">See also</span></span>

- [<span data-ttu-id="fef8a-123">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="fef8a-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="fef8a-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="fef8a-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
