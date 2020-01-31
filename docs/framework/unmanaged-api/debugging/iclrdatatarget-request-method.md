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
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793697"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="4e19b-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="4e19b-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="4e19b-103">由 common language runtime （CLR）資料存取服務呼叫，以要求作業，如實作為所定義。</span><span class="sxs-lookup"><span data-stu-id="4e19b-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e19b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e19b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e19b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e19b-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="4e19b-106">在使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="4e19b-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="4e19b-107">在輸入緩衝區的大小，用於傳入的要求。</span><span class="sxs-lookup"><span data-stu-id="4e19b-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="4e19b-108">在包含要求的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4e19b-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="4e19b-109">在輸出緩衝區的大小，用於回應。</span><span class="sxs-lookup"><span data-stu-id="4e19b-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="4e19b-110">脫銷包含回應的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4e19b-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e19b-111">備註</span><span class="sxs-lookup"><span data-stu-id="4e19b-111">Remarks</span></span>  
 <span data-ttu-id="4e19b-112">`Request` 方法可協助新增未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="4e19b-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="4e19b-113">也就是說，這個方法會提供擴充性，而不需要修改介面定義。</span><span class="sxs-lookup"><span data-stu-id="4e19b-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="4e19b-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="4e19b-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e19b-115">需求</span><span class="sxs-lookup"><span data-stu-id="4e19b-115">Requirements</span></span>  
 <span data-ttu-id="4e19b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e19b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e19b-117">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="4e19b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4e19b-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e19b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e19b-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e19b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e19b-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e19b-120">See also</span></span>

- [<span data-ttu-id="4e19b-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="4e19b-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
