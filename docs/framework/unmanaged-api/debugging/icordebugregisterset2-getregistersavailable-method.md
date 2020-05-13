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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378213"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="3fcac-102">ICorDebugRegisterSet2::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="3fcac-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="3fcac-103">取得提供可用暫存器之點陣圖的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3fcac-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcac-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fcac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fcac-105">參數</span><span class="sxs-lookup"><span data-stu-id="3fcac-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="3fcac-106">[in] `availableRegChunks` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3fcac-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="3fcac-107">脫銷位元組陣列，其中每個位對應至暫存器。</span><span class="sxs-lookup"><span data-stu-id="3fcac-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="3fcac-108">如果有可用的註冊，則會設定暫存器的對應位。</span><span class="sxs-lookup"><span data-stu-id="3fcac-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fcac-109">備註</span><span class="sxs-lookup"><span data-stu-id="3fcac-109">Remarks</span></span>  
 <span data-ttu-id="3fcac-110">CorDebugRegister 列舉的值會指定不同微處理器的暫存器。</span><span class="sxs-lookup"><span data-stu-id="3fcac-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="3fcac-111">每個值的前五個位是位元組陣列中的索引 `availableRegChunks` 。</span><span class="sxs-lookup"><span data-stu-id="3fcac-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="3fcac-112">每個值的較低三個位識別索引位元組內的位位置。</span><span class="sxs-lookup"><span data-stu-id="3fcac-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="3fcac-113">假設有一個指定特定暫存器的 `CorDebugRegister` 值，則會以下列方式決定登錄在遮罩中的位置：</span><span class="sxs-lookup"><span data-stu-id="3fcac-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="3fcac-114">解壓縮存取陣列中正確位元組所需的索引 `availableRegChunks` ：</span><span class="sxs-lookup"><span data-stu-id="3fcac-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="3fcac-115">`CorDebugRegister`值 >> 3</span><span class="sxs-lookup"><span data-stu-id="3fcac-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="3fcac-116">將索引位元組中的位位置解壓縮，其中 bit 零是最不重要的位：</span><span class="sxs-lookup"><span data-stu-id="3fcac-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="3fcac-117">`CorDebugRegister`值 & 7</span><span class="sxs-lookup"><span data-stu-id="3fcac-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fcac-118">需求</span><span class="sxs-lookup"><span data-stu-id="3fcac-118">Requirements</span></span>  
 <span data-ttu-id="3fcac-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fcac-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fcac-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fcac-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fcac-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fcac-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fcac-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fcac-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcac-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fcac-123">See also</span></span>

- [<span data-ttu-id="3fcac-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="3fcac-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="3fcac-125">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="3fcac-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
