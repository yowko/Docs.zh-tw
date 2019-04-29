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
ms.openlocfilehash: e9005dd8fde0d7258bd1dd48b561e4925e87733b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698066"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="b0554-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="b0554-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="b0554-103">由通用語言執行平台 (CLR) 資料存取服務要求的作業，呼叫，實作所定義。</span><span class="sxs-lookup"><span data-stu-id="b0554-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0554-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0554-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b0554-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0554-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="b0554-106">[in]使用者定義。</span><span class="sxs-lookup"><span data-stu-id="b0554-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="b0554-107">[in]輸入緩衝區，用於連入要求的大小。</span><span class="sxs-lookup"><span data-stu-id="b0554-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="b0554-108">[in]包含要求的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b0554-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="b0554-109">[in]輸出緩衝區，它用於回應的大小。</span><span class="sxs-lookup"><span data-stu-id="b0554-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="b0554-110">[out]包含回應的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b0554-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0554-111">備註</span><span class="sxs-lookup"><span data-stu-id="b0554-111">Remarks</span></span>  
 <span data-ttu-id="b0554-112">`Request`方法可協助的未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="b0554-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="b0554-113">也就是說，這個方法會提供擴充性，而不需要的介面定義的修訂。</span><span class="sxs-lookup"><span data-stu-id="b0554-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="b0554-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="b0554-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0554-115">需求</span><span class="sxs-lookup"><span data-stu-id="b0554-115">Requirements</span></span>  
 <span data-ttu-id="b0554-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0554-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0554-117">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b0554-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b0554-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0554-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0554-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0554-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0554-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0554-120">See also</span></span>

- [<span data-ttu-id="b0554-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="b0554-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
