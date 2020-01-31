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
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792112"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="1bfdc-102">ICorDebugRegisterSet::GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="1bfdc-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="1bfdc-103">取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bfdc-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bfdc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bfdc-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bfdc-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="1bfdc-106">在位元遮罩，指定要抓取的暫存器值。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="1bfdc-107">每個位都會對應到一個暫存器。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="1bfdc-108">如果位設為1，則會抓取暫存器的值;否則，就不會抓取暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="1bfdc-109">在要抓取的暫存器值數目。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="1bfdc-110">脫銷`CORDB_REGISTER` 物件的陣列，其中每一個都會接收暫存器的值。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bfdc-111">備註</span><span class="sxs-lookup"><span data-stu-id="1bfdc-111">Remarks</span></span>  
 <span data-ttu-id="1bfdc-112">陣列的大小應該等於位元遮罩中設定為一個的位數。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="1bfdc-113">`regCount` 參數會指定將接收暫存器值之緩衝區中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="1bfdc-114">如果 `regCount` 值對遮罩所指示的暫存器數目而言太小，則會從集合中截斷編號較高的暫存器。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="1bfdc-115">如果 `regCount` 值太大，則不會修改未使用的 `regBuffer` 元素。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="1bfdc-116">如果位元遮罩指定的暫存器無法使用，`GetRegisters` 會傳回該暫存器的不定值。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bfdc-117">需求</span><span class="sxs-lookup"><span data-stu-id="1bfdc-117">Requirements</span></span>  
 <span data-ttu-id="1bfdc-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bfdc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bfdc-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bfdc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bfdc-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bfdc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bfdc-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bfdc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bfdc-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="1bfdc-122">See also</span></span>

- [<span data-ttu-id="1bfdc-123">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="1bfdc-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="1bfdc-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="1bfdc-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
