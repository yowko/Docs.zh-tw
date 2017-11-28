---
title: "ICLRDataTarget::Request 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.Request
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e0ce905ea21267419e6a68e73f918de8fc364f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="58f2e-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="58f2e-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="58f2e-103">由通用語言執行平台 (CLR) 資料存取服務要求的操作，實作所定義。</span><span class="sxs-lookup"><span data-stu-id="58f2e-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="58f2e-104">Syntax</span></span>  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58f2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="58f2e-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="58f2e-106">[in]使用者定義。</span><span class="sxs-lookup"><span data-stu-id="58f2e-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="58f2e-107">[in]輸入緩衝區，用於連入要求的大小。</span><span class="sxs-lookup"><span data-stu-id="58f2e-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="58f2e-108">[in]包含要求之緩衝區。</span><span class="sxs-lookup"><span data-stu-id="58f2e-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="58f2e-109">[in]輸出緩衝區，用來回應的大小。</span><span class="sxs-lookup"><span data-stu-id="58f2e-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="58f2e-110">[out]包含回應緩衝區。</span><span class="sxs-lookup"><span data-stu-id="58f2e-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58f2e-111">備註</span><span class="sxs-lookup"><span data-stu-id="58f2e-111">Remarks</span></span>  
 <span data-ttu-id="58f2e-112">`Request`方法可協助加入未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="58f2e-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="58f2e-113">也就是說，這個方法會提供擴充性而不需要的介面定義的修訂。</span><span class="sxs-lookup"><span data-stu-id="58f2e-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="58f2e-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="58f2e-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f2e-115">需求</span><span class="sxs-lookup"><span data-stu-id="58f2e-115">Requirements</span></span>  
 <span data-ttu-id="58f2e-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58f2e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f2e-117">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="58f2e-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="58f2e-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58f2e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58f2e-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f2e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f2e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f2e-120">See Also</span></span>  
 [<span data-ttu-id="58f2e-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="58f2e-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
