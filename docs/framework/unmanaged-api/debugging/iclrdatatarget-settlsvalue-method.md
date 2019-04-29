---
title: ICLRDataTarget::SetTLSValue 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0be35772b10d89f90da5b33f47aa781034b13a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698079"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="865dc-102">ICLRDataTarget::SetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="865dc-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="865dc-103">設定執行緒區域儲存區 (TLS) 的目標處理序中指定的執行緒中的值。</span><span class="sxs-lookup"><span data-stu-id="865dc-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="865dc-104">這個方法是由通用語言執行平台 (CLR) 資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="865dc-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865dc-105">語法</span><span class="sxs-lookup"><span data-stu-id="865dc-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865dc-106">參數</span><span class="sxs-lookup"><span data-stu-id="865dc-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="865dc-107">[in]目標處理序中的執行緒作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="865dc-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="865dc-108">[in]位置的索引。</span><span class="sxs-lookup"><span data-stu-id="865dc-108">[in] The index of the location.</span></span> <span data-ttu-id="865dc-109">此值必須是執行緒的指定本機存放區中的有效索引。</span><span class="sxs-lookup"><span data-stu-id="865dc-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="865dc-110">[in]A`CLRDATA_ADDRESS`值，指定要放置在指定的 TLS 位置的值。</span><span class="sxs-lookup"><span data-stu-id="865dc-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865dc-111">備註</span><span class="sxs-lookup"><span data-stu-id="865dc-111">Remarks</span></span>  
 <span data-ttu-id="865dc-112">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="865dc-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865dc-113">需求</span><span class="sxs-lookup"><span data-stu-id="865dc-113">Requirements</span></span>  
 <span data-ttu-id="865dc-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="865dc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865dc-115">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="865dc-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="865dc-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="865dc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865dc-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865dc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="865dc-118">See also</span></span>

- [<span data-ttu-id="865dc-119">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="865dc-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
