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
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131362"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="38bae-102">ICorDebugRegisterSet2::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="38bae-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="38bae-103">取得提供可用暫存器之點陣圖的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="38bae-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38bae-104">語法</span><span class="sxs-lookup"><span data-stu-id="38bae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38bae-105">參數</span><span class="sxs-lookup"><span data-stu-id="38bae-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="38bae-106">[in] `availableRegChunks` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="38bae-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="38bae-107">脫銷位元組陣列，其中每個位對應至暫存器。</span><span class="sxs-lookup"><span data-stu-id="38bae-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="38bae-108">如果有可用的註冊，則會設定暫存器的對應位。</span><span class="sxs-lookup"><span data-stu-id="38bae-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38bae-109">備註</span><span class="sxs-lookup"><span data-stu-id="38bae-109">Remarks</span></span>  
 <span data-ttu-id="38bae-110">CorDebugRegister 列舉的值會指定不同微處理器的暫存器。</span><span class="sxs-lookup"><span data-stu-id="38bae-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="38bae-111">每個值的前五個位是 `availableRegChunks` 位元組陣列中的索引。</span><span class="sxs-lookup"><span data-stu-id="38bae-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="38bae-112">每個值的較低三個位識別索引位元組內的位位置。</span><span class="sxs-lookup"><span data-stu-id="38bae-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="38bae-113">假設有一個指定特定暫存器的 `CorDebugRegister` 值，則會以下列方式決定登錄在遮罩中的位置：</span><span class="sxs-lookup"><span data-stu-id="38bae-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="38bae-114">解壓縮存取 `availableRegChunks` 陣列中正確位元組所需的索引：</span><span class="sxs-lookup"><span data-stu-id="38bae-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="38bae-115">`CorDebugRegister` 值 > > 3</span><span class="sxs-lookup"><span data-stu-id="38bae-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="38bae-116">將索引位元組中的位位置解壓縮，其中 bit 零是最不重要的位：</span><span class="sxs-lookup"><span data-stu-id="38bae-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="38bae-117">`CorDebugRegister` 值 & 7</span><span class="sxs-lookup"><span data-stu-id="38bae-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38bae-118">需求</span><span class="sxs-lookup"><span data-stu-id="38bae-118">Requirements</span></span>  
 <span data-ttu-id="38bae-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38bae-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38bae-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38bae-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38bae-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38bae-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38bae-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38bae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bae-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="38bae-123">See also</span></span>

- [<span data-ttu-id="38bae-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="38bae-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="38bae-125">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="38bae-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
