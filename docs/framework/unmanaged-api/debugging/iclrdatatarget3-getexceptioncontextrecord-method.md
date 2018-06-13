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
ms.openlocfilehash: 1b07318406268023e2d66259b2cb68750d64613e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408160"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="75f8f-102">ICLRDataTarget3::GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="75f8f-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="75f8f-103">由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="75f8f-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="75f8f-104">例如，針對傾印目標，這會是相當於透過內容記錄`ExceptionParam`引數[MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) Windows Debug Help Library (DbgHelp) 中的函式。</span><span class="sxs-lookup"><span data-stu-id="75f8f-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f8f-105">語法</span><span class="sxs-lookup"><span data-stu-id="75f8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75f8f-106">參數</span><span class="sxs-lookup"><span data-stu-id="75f8f-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="75f8f-107">[in] 輸入緩衝區大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="75f8f-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="75f8f-108">這必須夠大，以容納內容記錄。</span><span class="sxs-lookup"><span data-stu-id="75f8f-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="75f8f-109">[out] `ULONG32` 類型的指標，此類型會接收實際寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="75f8f-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="75f8f-110">[out] 接收內容記錄複本之記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="75f8f-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="75f8f-111">例外狀況記錄會當成[內容](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)型別。</span><span class="sxs-lookup"><span data-stu-id="75f8f-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75f8f-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="75f8f-112">Return Value</span></span>  
 <span data-ttu-id="75f8f-113">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="75f8f-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="75f8f-114">`HRESULT` 程式碼可以包括 (但不限於) 下列項目：</span><span class="sxs-lookup"><span data-stu-id="75f8f-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="75f8f-115">傳回碼</span><span class="sxs-lookup"><span data-stu-id="75f8f-115">Return code</span></span>|<span data-ttu-id="75f8f-116">描述</span><span class="sxs-lookup"><span data-stu-id="75f8f-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="75f8f-117">方法成功。</span><span class="sxs-lookup"><span data-stu-id="75f8f-117">Method succeeded.</span></span> <span data-ttu-id="75f8f-118">內容記錄已複製到輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="75f8f-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="75f8f-119">沒有與目標相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="75f8f-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="75f8f-120">輸入緩衝區大小不夠大，無法容納內容記錄。</span><span class="sxs-lookup"><span data-stu-id="75f8f-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f8f-121">備註</span><span class="sxs-lookup"><span data-stu-id="75f8f-121">Remarks</span></span>  
 <span data-ttu-id="75f8f-122">[內容](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)是 Windows SDK 所提供的標頭中定義的特定平台結構。</span><span class="sxs-lookup"><span data-stu-id="75f8f-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="75f8f-123">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="75f8f-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f8f-124">需求</span><span class="sxs-lookup"><span data-stu-id="75f8f-124">Requirements</span></span>  
 <span data-ttu-id="75f8f-125">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75f8f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f8f-126">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="75f8f-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="75f8f-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f8f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f8f-128">**.NET framework 版本：** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f8f-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f8f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75f8f-129">See Also</span></span>  
 [<span data-ttu-id="75f8f-130">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="75f8f-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="75f8f-131">GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="75f8f-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="75f8f-132">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="75f8f-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
