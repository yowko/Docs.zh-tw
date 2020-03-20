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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179118"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="0a52d-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="0a52d-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="0a52d-103">由通用語言運行時 （CLR） 資料訪問服務調用，以請求由實現定義的操作。</span><span class="sxs-lookup"><span data-stu-id="0a52d-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a52d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a52d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="0a52d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a52d-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="0a52d-106">[在]使用者定義。</span><span class="sxs-lookup"><span data-stu-id="0a52d-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="0a52d-107">[在]用於傳入請求的輸入緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="0a52d-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="0a52d-108">[在]包含請求的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0a52d-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="0a52d-109">[在]用於回應的輸出緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="0a52d-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="0a52d-110">[出]包含回應的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0a52d-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a52d-111">備註</span><span class="sxs-lookup"><span data-stu-id="0a52d-111">Remarks</span></span>  
 <span data-ttu-id="0a52d-112">該方法`Request`便於添加未指定的自訂操作。</span><span class="sxs-lookup"><span data-stu-id="0a52d-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="0a52d-113">也就是說，此方法提供可擴充性，而無需修訂介面定義。</span><span class="sxs-lookup"><span data-stu-id="0a52d-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="0a52d-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="0a52d-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a52d-115">需求</span><span class="sxs-lookup"><span data-stu-id="0a52d-115">Requirements</span></span>  
 <span data-ttu-id="0a52d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a52d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a52d-117">**標題：** ClrData.idl， ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0a52d-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0a52d-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a52d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a52d-119">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a52d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a52d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a52d-120">See also</span></span>

- [<span data-ttu-id="0a52d-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0a52d-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
