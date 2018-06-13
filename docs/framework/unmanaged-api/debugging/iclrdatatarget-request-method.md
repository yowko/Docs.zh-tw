---
title: ICLRDataTarget::Request 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc79277c75118b11766e66137284bd5655eed091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405368"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="4269f-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="4269f-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="4269f-103">由通用語言執行平台 (CLR) 資料存取服務要求的操作，實作所定義。</span><span class="sxs-lookup"><span data-stu-id="4269f-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4269f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4269f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4269f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4269f-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="4269f-106">[in]使用者定義。</span><span class="sxs-lookup"><span data-stu-id="4269f-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="4269f-107">[in]輸入緩衝區，用於連入要求的大小。</span><span class="sxs-lookup"><span data-stu-id="4269f-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="4269f-108">[in]包含要求之緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4269f-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="4269f-109">[in]輸出緩衝區，用來回應的大小。</span><span class="sxs-lookup"><span data-stu-id="4269f-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="4269f-110">[out]包含回應緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4269f-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4269f-111">備註</span><span class="sxs-lookup"><span data-stu-id="4269f-111">Remarks</span></span>  
 <span data-ttu-id="4269f-112">`Request`方法可協助加入未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="4269f-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="4269f-113">也就是說，這個方法會提供擴充性而不需要的介面定義的修訂。</span><span class="sxs-lookup"><span data-stu-id="4269f-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="4269f-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="4269f-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4269f-115">需求</span><span class="sxs-lookup"><span data-stu-id="4269f-115">Requirements</span></span>  
 <span data-ttu-id="4269f-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4269f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4269f-117">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4269f-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4269f-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4269f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4269f-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4269f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4269f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4269f-120">See Also</span></span>  
 [<span data-ttu-id="4269f-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="4269f-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
