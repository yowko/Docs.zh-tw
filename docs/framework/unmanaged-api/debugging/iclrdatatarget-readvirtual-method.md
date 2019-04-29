---
title: ICLRDataTarget::ReadVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e2ec063d46ce9c890927391107888032e31378
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698092"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="08a63-102">ICLRDataTarget::ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="08a63-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="08a63-103">讀取指定的虛擬記憶體位址的資料儲存至指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="08a63-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a63-104">語法</span><span class="sxs-lookup"><span data-stu-id="08a63-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08a63-105">參數</span><span class="sxs-lookup"><span data-stu-id="08a63-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="08a63-106">[in]CLRDATA_ADDRESS 儲存的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="08a63-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="08a63-107">[out]接收資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="08a63-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="08a63-108">[in]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="08a63-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="08a63-109">[out]傳回的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="08a63-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a63-110">需求</span><span class="sxs-lookup"><span data-stu-id="08a63-110">Requirements</span></span>  
 <span data-ttu-id="08a63-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08a63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a63-112">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="08a63-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="08a63-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08a63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08a63-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a63-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08a63-115">See also</span></span>

- [<span data-ttu-id="08a63-116">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="08a63-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
