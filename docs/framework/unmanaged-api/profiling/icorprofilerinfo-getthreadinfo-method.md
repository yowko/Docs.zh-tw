---
title: ICorProfilerInfo::GetThreadInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0631afe149c7a179a6cda4b5e491ad28653ddee9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111913"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="de996-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="de996-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="de996-103">取得指定的執行緒目前的 Win32 執行緒身分識別。</span><span class="sxs-lookup"><span data-stu-id="de996-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de996-104">語法</span><span class="sxs-lookup"><span data-stu-id="de996-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de996-105">參數</span><span class="sxs-lookup"><span data-stu-id="de996-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="de996-106">[in]要取得目前的 Win32 ID 的執行緒識別碼</span><span class="sxs-lookup"><span data-stu-id="de996-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="de996-107">[out]指向指定的執行緒目前的 Win32 執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="de996-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de996-108">需求</span><span class="sxs-lookup"><span data-stu-id="de996-108">Requirements</span></span>  
 <span data-ttu-id="de996-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de996-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de996-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de996-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de996-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de996-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="de996-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="de996-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="de996-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de996-113">See also</span></span>

- [<span data-ttu-id="de996-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="de996-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
