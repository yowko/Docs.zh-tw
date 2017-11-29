---
title: "ICorDebugRegisterSet2::GetRegistersAvailable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="a63fd-102">ICorDebugRegisterSet2::GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="a63fd-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="a63fd-103">取得位元組陣列提供的可用暫存器的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="a63fd-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="a63fd-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a63fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="a63fd-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="a63fd-106">[in] `availableRegChunks` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a63fd-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="a63fd-107">[out]位元組陣列，其中每個位元對應暫存器。</span><span class="sxs-lookup"><span data-stu-id="a63fd-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="a63fd-108">如果使用暫存器，則會設定暫存器的對應位元。</span><span class="sxs-lookup"><span data-stu-id="a63fd-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63fd-109">備註</span><span class="sxs-lookup"><span data-stu-id="a63fd-109">Remarks</span></span>  
 <span data-ttu-id="a63fd-110">CorDebugRegister 列舉的值會指定不同的微處理器的暫存器。</span><span class="sxs-lookup"><span data-stu-id="a63fd-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="a63fd-111">每個值的上方的五個位元皆為的索引`availableRegChunks`的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a63fd-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="a63fd-112">每個值的較低的三位元會識別索引位元組中的位元位置。</span><span class="sxs-lookup"><span data-stu-id="a63fd-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="a63fd-113">指定`CorDebugRegister`指定特定的暫存器，遮罩中的暫存位置的值決定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a63fd-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="a63fd-114">擷取存取正確的位元組中所需的索引`availableRegChunks`陣列：</span><span class="sxs-lookup"><span data-stu-id="a63fd-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="a63fd-115">`CorDebugRegister`值 >> 3</span><span class="sxs-lookup"><span data-stu-id="a63fd-115">`CorDebugRegister` value >> 3</span></span>  
  
2.  <span data-ttu-id="a63fd-116">擷取其中位元 0 是最小顯著性位元的位元位置內的索引的位元組：</span><span class="sxs-lookup"><span data-stu-id="a63fd-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="a63fd-117">`CorDebugRegister`值 （& s) 7</span><span class="sxs-lookup"><span data-stu-id="a63fd-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63fd-118">需求</span><span class="sxs-lookup"><span data-stu-id="a63fd-118">Requirements</span></span>  
 <span data-ttu-id="a63fd-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a63fd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63fd-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a63fd-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a63fd-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a63fd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a63fd-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63fd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a63fd-123">See Also</span></span>  
 [<span data-ttu-id="a63fd-124">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="a63fd-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="a63fd-125">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="a63fd-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
