---
title: ICLRDataTarget3::GetExceptionThreadID 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697897"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="b6ebe-102">ICLRDataTarget3::GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="b6ebe-103">由通用語言執行平台 (CLR) 資料存取服務呼叫，以取得擲回例外狀況之執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ebe-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ebe-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6ebe-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b6ebe-106">[out] 擲回例外狀況之執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6ebe-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6ebe-107">Return Value</span></span>  
 <span data-ttu-id="b6ebe-108">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b6ebe-109">`HRESULT` 程式碼可以包括 (但不限於) 下列項目：</span><span class="sxs-lookup"><span data-stu-id="b6ebe-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="b6ebe-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="b6ebe-110">Return code</span></span>|<span data-ttu-id="b6ebe-111">描述</span><span class="sxs-lookup"><span data-stu-id="b6ebe-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b6ebe-112">方法成功。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="b6ebe-113">找不到例外狀況的有效執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6ebe-114">備註</span><span class="sxs-lookup"><span data-stu-id="b6ebe-114">Remarks</span></span>  
 <span data-ttu-id="b6ebe-115">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ebe-116">需求</span><span class="sxs-lookup"><span data-stu-id="b6ebe-116">Requirements</span></span>  
 <span data-ttu-id="b6ebe-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ebe-118">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b6ebe-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b6ebe-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ebe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ebe-120">**.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ebe-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ebe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6ebe-121">See also</span></span>

- [<span data-ttu-id="b6ebe-122">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="b6ebe-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="b6ebe-123">GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="b6ebe-124">GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
