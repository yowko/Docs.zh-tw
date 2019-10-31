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
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113346"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="02afc-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="02afc-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="02afc-103">由 common language runtime （CLR）資料存取服務呼叫，以要求作業，如實作為所定義。</span><span class="sxs-lookup"><span data-stu-id="02afc-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02afc-104">語法</span><span class="sxs-lookup"><span data-stu-id="02afc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="02afc-105">參數</span><span class="sxs-lookup"><span data-stu-id="02afc-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="02afc-106">在使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="02afc-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="02afc-107">在輸入緩衝區的大小，用於傳入的要求。</span><span class="sxs-lookup"><span data-stu-id="02afc-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="02afc-108">在包含要求的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="02afc-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="02afc-109">在輸出緩衝區的大小，用於回應。</span><span class="sxs-lookup"><span data-stu-id="02afc-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="02afc-110">脫銷包含回應的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="02afc-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02afc-111">備註</span><span class="sxs-lookup"><span data-stu-id="02afc-111">Remarks</span></span>  
 <span data-ttu-id="02afc-112">`Request` 方法可協助新增未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="02afc-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="02afc-113">也就是說，這個方法會提供擴充性，而不需要修改介面定義。</span><span class="sxs-lookup"><span data-stu-id="02afc-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="02afc-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="02afc-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02afc-115">需求</span><span class="sxs-lookup"><span data-stu-id="02afc-115">Requirements</span></span>  
 <span data-ttu-id="02afc-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02afc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02afc-117">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="02afc-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="02afc-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02afc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02afc-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02afc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02afc-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="02afc-120">See also</span></span>

- [<span data-ttu-id="02afc-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="02afc-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
