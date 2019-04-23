---
title: ICLRDataTarget::GetTLSValue 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fa9a17067f754fe9b13c4d32193856a57750ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227362"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="c3ae9-102">ICLRDataTarget::GetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="c3ae9-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="c3ae9-103">取得從執行緒區域儲存區 (TLS) 的值，指定目標處理序中執行緒。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c3ae9-104">這個方法是由通用語言執行平台 (CLR) 資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ae9-105">語法</span><span class="sxs-lookup"><span data-stu-id="c3ae9-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ae9-106">參數</span><span class="sxs-lookup"><span data-stu-id="c3ae9-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c3ae9-107">[in]目標處理序中的執行緒作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c3ae9-108">[in]位置的索引。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-108">[in] The index of the location.</span></span> <span data-ttu-id="c3ae9-109">此值必須是執行緒的指定本機存放區中的有效索引。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c3ae9-110">[out]指標`CLRDATA_ADDRESS`值，指定值傳回從指定的 TLS 位置。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ae9-111">備註</span><span class="sxs-lookup"><span data-stu-id="c3ae9-111">Remarks</span></span>  
 <span data-ttu-id="c3ae9-112">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ae9-113">需求</span><span class="sxs-lookup"><span data-stu-id="c3ae9-113">Requirements</span></span>  
 <span data-ttu-id="c3ae9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3ae9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ae9-115">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c3ae9-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c3ae9-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3ae9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ae9-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ae9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ae9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ae9-118">See also</span></span>

- [<span data-ttu-id="c3ae9-119">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="c3ae9-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
