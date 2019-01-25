---
title: ICLRDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540f9d1a765ff46235f3c3d62f5da4a00b8ab85a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745476"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="db9f5-102">ICLRDataTarget::WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="db9f5-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="db9f5-103">將資料從指定的緩衝區寫入指定的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="db9f5-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="db9f5-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db9f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="db9f5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="db9f5-106">[in]CLRDATA_ADDRESS 儲存的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="db9f5-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="db9f5-107">[in]將資料寫入緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="db9f5-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="db9f5-108">[in]要寫入的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="db9f5-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="db9f5-109">[out]實際寫入的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="db9f5-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db9f5-110">需求</span><span class="sxs-lookup"><span data-stu-id="db9f5-110">Requirements</span></span>  
 <span data-ttu-id="db9f5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db9f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db9f5-112">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="db9f5-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="db9f5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db9f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db9f5-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db9f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9f5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db9f5-115">See also</span></span>
- [<span data-ttu-id="db9f5-116">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="db9f5-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
