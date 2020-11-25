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
ms.openlocfilehash: 516a12b7a4457a0f67da24294ad96fb79d1aa5aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707512"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="e7078-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e7078-102">ICorProfilerInfo::GetThreadInfo Method</span></span>

<span data-ttu-id="e7078-103">取得指定執行緒目前的 Win32 執行緒識別。</span><span class="sxs-lookup"><span data-stu-id="e7078-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7078-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7078-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7078-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7078-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="e7078-106">在要取得目前 Win32 識別碼之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e7078-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="e7078-107">擴展指定執行緒目前的 Win32 執行緒識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="e7078-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7078-108">需求</span><span class="sxs-lookup"><span data-stu-id="e7078-108">Requirements</span></span>  

 <span data-ttu-id="e7078-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7078-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7078-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7078-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7078-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7078-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7078-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7078-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7078-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7078-113">See also</span></span>

- [<span data-ttu-id="e7078-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e7078-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
