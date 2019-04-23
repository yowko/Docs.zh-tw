---
title: ICorDebugRegisterSet2::GetRegistersAvailable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1522d643a69c47eec03770a8f51756dd4250075a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309416"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="7c9ee-102">ICorDebugRegisterSet2::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="7c9ee-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="7c9ee-103">取得位元組陣列，提供可用的暫存器的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c9ee-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c9ee-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="7c9ee-106">[in] `availableRegChunks` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="7c9ee-107">[out]位元組陣列，其中每個位元對應暫存器。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="7c9ee-108">如果使用暫存器，則會設定註冊的對應位元。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c9ee-109">備註</span><span class="sxs-lookup"><span data-stu-id="7c9ee-109">Remarks</span></span>  
 <span data-ttu-id="7c9ee-110">CorDebugRegister 列舉之值的指定不同的微處理器的暫存器。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="7c9ee-111">每個值的較高的五位元是索引`availableRegChunks`的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="7c9ee-112">每個值的較低的三位元識別索引位元組中的位元位置。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="7c9ee-113">指定`CorDebugRegister`值，指定特定的暫存器，用來遮罩中的暫存位置的判斷如下：</span><span class="sxs-lookup"><span data-stu-id="7c9ee-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="7c9ee-114">擷取存取中的正確位元組所需的索引`availableRegChunks`陣列：</span><span class="sxs-lookup"><span data-stu-id="7c9ee-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="7c9ee-115">`CorDebugRegister` 值 >> 3</span><span class="sxs-lookup"><span data-stu-id="7c9ee-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="7c9ee-116">擷取元零所在的最小顯著性的位元的位元位置內的索引的位元組：</span><span class="sxs-lookup"><span data-stu-id="7c9ee-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="7c9ee-117">`CorDebugRegister` 值 & 7</span><span class="sxs-lookup"><span data-stu-id="7c9ee-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9ee-118">需求</span><span class="sxs-lookup"><span data-stu-id="7c9ee-118">Requirements</span></span>  
 <span data-ttu-id="7c9ee-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c9ee-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9ee-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c9ee-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c9ee-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9ee-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9ee-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9ee-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9ee-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c9ee-123">See also</span></span>

- [<span data-ttu-id="7c9ee-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="7c9ee-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="7c9ee-125">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="7c9ee-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
