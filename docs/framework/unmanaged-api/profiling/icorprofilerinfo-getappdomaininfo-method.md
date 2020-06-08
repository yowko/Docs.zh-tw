---
title: ICorProfilerInfo::GetAppDomainInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503025"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="8a017-102">ICorProfilerInfo::GetAppDomainInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8a017-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="8a017-103">接受應用程式定義域 ID。</span><span class="sxs-lookup"><span data-stu-id="8a017-103">Accepts an application domain ID.</span></span> <span data-ttu-id="8a017-104">傳回應用程式定義域名稱和包含該處理序的 ID。</span><span class="sxs-lookup"><span data-stu-id="8a017-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a017-105">語法</span><span class="sxs-lookup"><span data-stu-id="8a017-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a017-106">參數</span><span class="sxs-lookup"><span data-stu-id="8a017-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8a017-107">[in] 應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="8a017-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a017-108">[in] `szName` 傳回緩衝區的長度 (以字元為單位)。</span><span class="sxs-lookup"><span data-stu-id="8a017-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8a017-109">[out] 應用程式定義域名稱之總字元長度的指標。</span><span class="sxs-lookup"><span data-stu-id="8a017-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a017-110">[out] 呼叫端提供的寬字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8a017-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="8a017-111">當此方法傳回時，`szName` 將包含完整或部分的應用程式定義域名稱。</span><span class="sxs-lookup"><span data-stu-id="8a017-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="8a017-112">[out] 包含應用程式定義域之處理序 ID 的指標。</span><span class="sxs-lookup"><span data-stu-id="8a017-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a017-113">備註</span><span class="sxs-lookup"><span data-stu-id="8a017-113">Remarks</span></span>  
 <span data-ttu-id="8a017-114">在此方法傳回之後，您必須確認 `szName` 緩衝區的大小足以包含應用程式定義域的完整檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8a017-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="8a017-115">若要這樣做，請比對 `pcchName` 指向的值和 `cchName` 參數。</span><span class="sxs-lookup"><span data-stu-id="8a017-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="8a017-116">如果 `pcchName` 指向大於 `cchName` 的值，請配置較大的 `szName` 緩衝區，並以較大的大小來更新 `cchName`，然後再次呼叫 `GetAppDomainInfo`。</span><span class="sxs-lookup"><span data-stu-id="8a017-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="8a017-117">或者，您也可以先使用長度為零的 `szName` 緩衝區來呼叫 `GetAppDomainInfo`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="8a017-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="8a017-118">接著您就可以將緩衝區大小設定為 `pcchName` 中傳回的值，並再次呼叫 `GetAppDomainInfo`。</span><span class="sxs-lookup"><span data-stu-id="8a017-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a017-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="8a017-119">Requirements</span></span>  
 <span data-ttu-id="8a017-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a017-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a017-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a017-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a017-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a017-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a017-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a017-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a017-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a017-124">See also</span></span>

- [<span data-ttu-id="8a017-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8a017-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8a017-126">分析介面</span><span class="sxs-lookup"><span data-stu-id="8a017-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8a017-127">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="8a017-127">Profiling</span></span>](index.md)
