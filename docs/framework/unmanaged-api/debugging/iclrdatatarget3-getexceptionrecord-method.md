---
title: "ICLRDataTarget3::GetExceptionRecord 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="9dfbb-102">ICLRDataTarget3::GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="9dfbb-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="9dfbb-103">由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="9dfbb-104">例如，針對傾印目標，這會是相當於透過例外狀況記錄`ExceptionParam`引數[MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) Windows Debug Help Library (DbgHelp) 中的函式。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dfbb-105">語法</span><span class="sxs-lookup"><span data-stu-id="9dfbb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dfbb-106">參數</span><span class="sxs-lookup"><span data-stu-id="9dfbb-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="9dfbb-107">[in] 輸入緩衝區大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="9dfbb-108">這必須等於`sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="9dfbb-109">[out] `ULONG32` 類型的指標，此類型會接收實際寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9dfbb-110">[out] 接收例外狀況記錄複本之記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="9dfbb-111">例外狀況記錄會當成[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)型別。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dfbb-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9dfbb-112">Return Value</span></span>  
 <span data-ttu-id="9dfbb-113">如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="9dfbb-114">`HRESULT` 程式碼可以包括 (但不限於) 下列項目：</span><span class="sxs-lookup"><span data-stu-id="9dfbb-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="9dfbb-115">傳回碼</span><span class="sxs-lookup"><span data-stu-id="9dfbb-115">Return code</span></span>|<span data-ttu-id="9dfbb-116">描述</span><span class="sxs-lookup"><span data-stu-id="9dfbb-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="9dfbb-117">方法成功。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-117">Method succeeded.</span></span> <span data-ttu-id="9dfbb-118">例外狀況記錄已複製到輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="9dfbb-119">沒有與目標相關聯的例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="9dfbb-120">輸入緩衝區大小等於 `sizeof(MINIDUMP_EXCEPTION)`。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dfbb-121">備註</span><span class="sxs-lookup"><span data-stu-id="9dfbb-121">Remarks</span></span>  
 <span data-ttu-id="9dfbb-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)是 dbghelp.h 及 imagehlp.h 中 Windows SDK 中所定義的結構。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="9dfbb-123">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dfbb-124">需求</span><span class="sxs-lookup"><span data-stu-id="9dfbb-124">Requirements</span></span>  
 <span data-ttu-id="9dfbb-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9dfbb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dfbb-126">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9dfbb-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9dfbb-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dfbb-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dfbb-128">**.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dfbb-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfbb-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="9dfbb-129">See Also</span></span>  
 [<span data-ttu-id="9dfbb-130">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="9dfbb-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="9dfbb-131">GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="9dfbb-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="9dfbb-132">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="9dfbb-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
