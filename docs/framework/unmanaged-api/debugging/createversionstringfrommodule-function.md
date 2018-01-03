---
title: "CreateVersionStringFromModule 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateVersionStringFromModule
api_location: dbgshim.dll
api_type: COM
f1_keywords: CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d7d545256393cfbe37216f0d6db064d5e7cb410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="fff4b-102">CreateVersionStringFromModule 函式</span><span class="sxs-lookup"><span data-stu-id="fff4b-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="fff4b-103">從目標處理序中的 Common Language Runtime (CLR) 路徑來建立版本字串。</span><span class="sxs-lookup"><span data-stu-id="fff4b-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fff4b-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fff4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="fff4b-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="fff4b-106">[in] 已載入目標 CLR 之處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fff4b-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="fff4b-107">[in] 載入處理序中之目標 CLR 的完整或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="fff4b-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="fff4b-108">[out] 用來儲存目標 CLR 之版本字串的傳回緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fff4b-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="fff4b-109">[in] `pBuffer` 的大小。</span><span class="sxs-lookup"><span data-stu-id="fff4b-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="fff4b-110">[out] `pBuffer` 傳回之版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="fff4b-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fff4b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fff4b-111">Return Value</span></span>  
 <span data-ttu-id="fff4b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fff4b-112">S_OK</span></span>  
 <span data-ttu-id="fff4b-113">目標 CLR 的版本字串已成功傳回 `pBuffer` 中。</span><span class="sxs-lookup"><span data-stu-id="fff4b-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="fff4b-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fff4b-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="fff4b-115">`szModuleName` 為 null，或者 `pBuffer` 或 `cchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="fff4b-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="fff4b-116">`pBuffer` 和 `cchBuffer` 必須都是 null 或非 null。</span><span class="sxs-lookup"><span data-stu-id="fff4b-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="fff4b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="fff4b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="fff4b-118">`pdwLength` 大於 `cchBuffer`。</span><span class="sxs-lookup"><span data-stu-id="fff4b-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="fff4b-119">如果您為 `pBuffer` 和 `cchBuffer` 傳遞 null，並使用 `pdwLength` 來查詢所需的緩衝區大小，這可能是預期的結果。</span><span class="sxs-lookup"><span data-stu-id="fff4b-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="fff4b-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="fff4b-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="fff4b-121">`szModuleName` 未包含目標處理序中有效 CLR 的路徑。</span><span class="sxs-lookup"><span data-stu-id="fff4b-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="fff4b-122">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="fff4b-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fff4b-123">`pidDebuggee` 未參考有效的處理序，或其他失敗。</span><span class="sxs-lookup"><span data-stu-id="fff4b-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff4b-124">備註</span><span class="sxs-lookup"><span data-stu-id="fff4b-124">Remarks</span></span>  
 <span data-ttu-id="fff4b-125">此函式可接受 `pidDebuggee` 識別的 CLR 處理序，以及 `szModuleName` 所指定的字串路徑。</span><span class="sxs-lookup"><span data-stu-id="fff4b-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="fff4b-126">版本字串傳回在 `pBuffer` 所指向的緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="fff4b-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="fff4b-127">此字串對函式使用者是不透明的，也就是說，版本字串本身沒有內建意義。</span><span class="sxs-lookup"><span data-stu-id="fff4b-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="fff4b-128">它只會用在這個函式和[CreateDebuggingInterfaceFromVersion 函式](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)。</span><span class="sxs-lookup"><span data-stu-id="fff4b-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="fff4b-129">應該要呼叫此函式兩次。</span><span class="sxs-lookup"><span data-stu-id="fff4b-129">This function should be called twice.</span></span> <span data-ttu-id="fff4b-130">當您第一次呼叫此函式時，針對 `pBuffer` 和 `cchBuffer` 都傳遞 null。</span><span class="sxs-lookup"><span data-stu-id="fff4b-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="fff4b-131">當您這麼做時，`pBuffer` 所需的緩衝區大小將會傳回 `pdwLength` 中。</span><span class="sxs-lookup"><span data-stu-id="fff4b-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="fff4b-132">然後您可以呼叫此函式第二次，並且在 `pBuffer` 中傳遞緩衝區，在 `cchBuffer` 中傳遞其大小。</span><span class="sxs-lookup"><span data-stu-id="fff4b-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff4b-133">需求</span><span class="sxs-lookup"><span data-stu-id="fff4b-133">Requirements</span></span>  
 <span data-ttu-id="fff4b-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fff4b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff4b-135">**標頭：** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="fff4b-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="fff4b-136">**程式庫：** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="fff4b-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="fff4b-137">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="fff4b-137">**.NET Framework Versions:** 3.5 SP1</span></span>
