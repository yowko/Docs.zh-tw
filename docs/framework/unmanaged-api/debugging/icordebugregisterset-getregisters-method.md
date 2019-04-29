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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782898"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="da43a-102">ICorDebugRegisterSet::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="da43a-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="da43a-103">取得每個暫存器值 （在電腦上目前正在執行的程式碼） 所指定的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="da43a-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da43a-104">語法</span><span class="sxs-lookup"><span data-stu-id="da43a-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da43a-105">參數</span><span class="sxs-lookup"><span data-stu-id="da43a-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="da43a-106">[in]位元遮罩，指定要擷取的值為哪一個暫存器。</span><span class="sxs-lookup"><span data-stu-id="da43a-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="da43a-107">每個位元對應暫存器。</span><span class="sxs-lookup"><span data-stu-id="da43a-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="da43a-108">如果位元設定為其中一個，就會擷取暫存器的值;否則，不會擷取暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="da43a-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="da43a-109">[in]要擷取的暫存器值數目。</span><span class="sxs-lookup"><span data-stu-id="da43a-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="da43a-110">[out]陣列`CORDB_REGISTER`物件，其中每個收到的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="da43a-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da43a-111">備註</span><span class="sxs-lookup"><span data-stu-id="da43a-111">Remarks</span></span>  
 <span data-ttu-id="da43a-112">陣列的大小應該是等於設為其中一個位元遮罩中的位元數。</span><span class="sxs-lookup"><span data-stu-id="da43a-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="da43a-113">`regCount`參數將會收到暫存器值之緩衝區中指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="da43a-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="da43a-114">如果`regCount`值遮罩所表示的暫存器數目太小，較高編號的暫存器會從集合中截斷。</span><span class="sxs-lookup"><span data-stu-id="da43a-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="da43a-115">如果`regCount`值太大，而未使用`regBuffer`項目將會是未修改。</span><span class="sxs-lookup"><span data-stu-id="da43a-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="da43a-116">如果位元遮罩指定的暫存器無法使用，`GetRegisters`傳回不定值，該暫存器。</span><span class="sxs-lookup"><span data-stu-id="da43a-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da43a-117">需求</span><span class="sxs-lookup"><span data-stu-id="da43a-117">Requirements</span></span>  
 <span data-ttu-id="da43a-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da43a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da43a-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da43a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da43a-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da43a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da43a-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da43a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da43a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da43a-122">See also</span></span>

- [<span data-ttu-id="da43a-123">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="da43a-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="da43a-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="da43a-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
