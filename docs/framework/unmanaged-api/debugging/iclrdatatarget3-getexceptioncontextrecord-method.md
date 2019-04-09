---
title: ICLRDataTarget3::GetExceptionContextRecord 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b43ab8cdeff3866bb51e8634f367cf86ee483d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089222"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="af447-102">ICLRDataTarget3::GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="af447-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="af447-103">由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="af447-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="af447-104">例如，針對傾印目標，這相當於透過傳入的內容記錄`ExceptionParam`引數[MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) Windows Debug Help Library (DbgHelp) 中的函式。</span><span class="sxs-lookup"><span data-stu-id="af447-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af447-105">語法</span><span class="sxs-lookup"><span data-stu-id="af447-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af447-106">參數</span><span class="sxs-lookup"><span data-stu-id="af447-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="af447-107">[in] 輸入緩衝區大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="af447-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="af447-108">這必須夠大，以容納內容記錄。</span><span class="sxs-lookup"><span data-stu-id="af447-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="af447-109">[out] `ULONG32` 類型的指標，此類型會接收實際寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="af447-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="af447-110">[out] 接收內容記錄複本之記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="af447-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="af447-111">例外狀況記錄會當成[內容](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)型別。</span><span class="sxs-lookup"><span data-stu-id="af447-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af447-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="af447-112">Return Value</span></span>  
 <span data-ttu-id="af447-113">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="af447-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="af447-114">`HRESULT` 程式碼可以包括 (但不限於) 下列項目：</span><span class="sxs-lookup"><span data-stu-id="af447-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="af447-115">傳回碼</span><span class="sxs-lookup"><span data-stu-id="af447-115">Return code</span></span>|<span data-ttu-id="af447-116">描述</span><span class="sxs-lookup"><span data-stu-id="af447-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="af447-117">方法成功。</span><span class="sxs-lookup"><span data-stu-id="af447-117">Method succeeded.</span></span> <span data-ttu-id="af447-118">內容記錄已複製到輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="af447-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="af447-119">沒有與目標相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="af447-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="af447-120">輸入緩衝區大小不夠大，無法容納內容記錄。</span><span class="sxs-lookup"><span data-stu-id="af447-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af447-121">備註</span><span class="sxs-lookup"><span data-stu-id="af447-121">Remarks</span></span>  
 <span data-ttu-id="af447-122">[內容](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)是 Windows SDK 所提供的標頭中定義的平台特定結構。</span><span class="sxs-lookup"><span data-stu-id="af447-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="af447-123">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="af447-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af447-124">需求</span><span class="sxs-lookup"><span data-stu-id="af447-124">Requirements</span></span>  
 <span data-ttu-id="af447-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af447-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af447-126">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="af447-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="af447-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af447-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af447-128">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="af447-128">.NET Framework Versions:</span></span>** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af447-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af447-129">See also</span></span>

- [<span data-ttu-id="af447-130">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="af447-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="af447-131">GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="af447-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="af447-132">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="af447-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
