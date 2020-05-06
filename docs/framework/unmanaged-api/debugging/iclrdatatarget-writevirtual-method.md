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
ms.openlocfilehash: 6a7a7736837f7e6bbf1ad4982e78a75550abbeab
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860497"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="ad7bf-102">ICLRDataTarget::WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="ad7bf-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="ad7bf-103">將資料從指定的緩衝區寫入指定的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad7bf-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad7bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad7bf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ad7bf-106">在儲存虛擬記憶體位址的 CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ad7bf-107">在儲存要寫入之資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="ad7bf-108">在要寫入的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="ad7bf-109">脫銷寫入的實際位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad7bf-110">需求</span><span class="sxs-lookup"><span data-stu-id="ad7bf-110">Requirements</span></span>  
 <span data-ttu-id="ad7bf-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad7bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7bf-112">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="ad7bf-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad7bf-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad7bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad7bf-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7bf-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad7bf-115">See also</span></span>

- [<span data-ttu-id="ad7bf-116">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="ad7bf-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
