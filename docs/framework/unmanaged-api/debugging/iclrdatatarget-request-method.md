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
ms.openlocfilehash: 4d0cf22b4b0644d6b25d6b3ef884718cb9ca1e42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723775"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="47517-102">ICLRDataTarget::Request 方法</span><span class="sxs-lookup"><span data-stu-id="47517-102">ICLRDataTarget::Request Method</span></span>

<span data-ttu-id="47517-103">由 common language runtime 呼叫 (CLR) 資料存取服務來要求作業，如實作為所定義。</span><span class="sxs-lookup"><span data-stu-id="47517-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47517-104">語法</span><span class="sxs-lookup"><span data-stu-id="47517-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="47517-105">參數</span><span class="sxs-lookup"><span data-stu-id="47517-105">Parameters</span></span>  

 `reqCode`  
 <span data-ttu-id="47517-106">在使用者定義。</span><span class="sxs-lookup"><span data-stu-id="47517-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="47517-107">在輸入緩衝區的大小，用於傳入要求。</span><span class="sxs-lookup"><span data-stu-id="47517-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="47517-108">在包含要求的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="47517-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="47517-109">在輸出緩衝區的大小，用於回應。</span><span class="sxs-lookup"><span data-stu-id="47517-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="47517-110">擴展包含回應的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="47517-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47517-111">備註</span><span class="sxs-lookup"><span data-stu-id="47517-111">Remarks</span></span>  

 <span data-ttu-id="47517-112">`Request`方法可協助新增未指定的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="47517-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="47517-113">也就是說，這個方法會提供擴充性，而不需要介面定義的修訂。</span><span class="sxs-lookup"><span data-stu-id="47517-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="47517-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="47517-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47517-115">需求</span><span class="sxs-lookup"><span data-stu-id="47517-115">Requirements</span></span>  

 <span data-ttu-id="47517-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47517-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47517-117">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="47517-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="47517-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47517-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47517-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47517-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47517-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47517-120">See also</span></span>

- [<span data-ttu-id="47517-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="47517-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
