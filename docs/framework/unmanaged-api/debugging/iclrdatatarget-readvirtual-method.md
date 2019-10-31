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
ms.openlocfilehash: 0c26a2df3f73af5ebd1f8b735d7662bb23ba4228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134169"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="0c078-102">ICLRDataTarget::ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="0c078-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="0c078-103">將資料從指定的虛擬記憶體位址讀入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0c078-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c078-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c078-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c078-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c078-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0c078-106">在儲存虛擬記憶體位址的 CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="0c078-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0c078-107">脫銷接收資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="0c078-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="0c078-108">在緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="0c078-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="0c078-109">脫銷傳回位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="0c078-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c078-110">需求</span><span class="sxs-lookup"><span data-stu-id="0c078-110">Requirements</span></span>  
 <span data-ttu-id="0c078-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c078-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c078-112">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="0c078-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0c078-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c078-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c078-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c078-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c078-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c078-115">See also</span></span>

- [<span data-ttu-id="0c078-116">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0c078-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
