---
title: ICorProfilerInfo3::GetRuntimeInformation 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164927"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="54d3b-102">ICorProfilerInfo3::GetRuntimeInformation 方法</span><span class="sxs-lookup"><span data-stu-id="54d3b-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="54d3b-103">提供 common language runtime (CLR) 所分析的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="54d3b-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="54d3b-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54d3b-105">參數</span><span class="sxs-lookup"><span data-stu-id="54d3b-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="54d3b-106">[out]代表處理序中執行 CLR 執行個體的識別碼。</span><span class="sxs-lookup"><span data-stu-id="54d3b-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="54d3b-107">這是與相同`ClrInstanceID`Windows (ETW) 啟動事件的事件追蹤報告。</span><span class="sxs-lookup"><span data-stu-id="54d3b-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="54d3b-108">[out]執行階段型別。</span><span class="sxs-lookup"><span data-stu-id="54d3b-108">[out] The runtime type.</span></span> <span data-ttu-id="54d3b-109">此參數會傳回`COR_PRF_DESKTOP_CLR`桌面版本的 CLR 或`COR_PRF_CORE_CLR`CLR 在 Silverlight 中使用的核心版本。</span><span class="sxs-lookup"><span data-stu-id="54d3b-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="54d3b-110">[out]CLR 的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="54d3b-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="54d3b-111">[out]CLR 的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="54d3b-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="54d3b-112">[out]CLR 組建版本號碼。</span><span class="sxs-lookup"><span data-stu-id="54d3b-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="54d3b-113">[out]軟體更新相關聯的 clr 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="54d3b-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="54d3b-114">[in]長度，以字元為單位的緩衝區，`szVersionString`指向。</span><span class="sxs-lookup"><span data-stu-id="54d3b-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="54d3b-115">[out]長度，以字元為單位的`szVersionString`。</span><span class="sxs-lookup"><span data-stu-id="54d3b-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="54d3b-116">[out]CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="54d3b-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54d3b-117">備註</span><span class="sxs-lookup"><span data-stu-id="54d3b-117">Remarks</span></span>  
 <span data-ttu-id="54d3b-118">您可以傳遞任何參數為 null。</span><span class="sxs-lookup"><span data-stu-id="54d3b-118">You may pass null for any parameter.</span></span> <span data-ttu-id="54d3b-119">不過，`pcchVersionString`不得為 null 除非`szVersionString`也是 null。</span><span class="sxs-lookup"><span data-stu-id="54d3b-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d3b-120">需求</span><span class="sxs-lookup"><span data-stu-id="54d3b-120">Requirements</span></span>  
 <span data-ttu-id="54d3b-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54d3b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d3b-122">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54d3b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54d3b-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54d3b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54d3b-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d3b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d3b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d3b-125">See also</span></span>

- [<span data-ttu-id="54d3b-126">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="54d3b-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="54d3b-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="54d3b-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="54d3b-128">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="54d3b-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
