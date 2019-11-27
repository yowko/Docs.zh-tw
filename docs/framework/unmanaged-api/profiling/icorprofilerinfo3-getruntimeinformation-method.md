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
ms.openlocfilehash: 20556d85655a0a1bbe069a94b99c19c774a13ce6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449689"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="a07a7-102">ICorProfilerInfo3::GetRuntimeInformation 方法</span><span class="sxs-lookup"><span data-stu-id="a07a7-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="a07a7-103">提供所分析之 common language runtime （CLR）的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a07a7-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a07a7-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a07a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="a07a7-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="a07a7-106">脫銷進程中執行中 CLR 實例的代表識別碼。</span><span class="sxs-lookup"><span data-stu-id="a07a7-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="a07a7-107">這與 Windows 事件追蹤（ETW）啟動附隨報告的 `ClrInstanceID` 相同。</span><span class="sxs-lookup"><span data-stu-id="a07a7-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="a07a7-108">脫銷執行時間類型。</span><span class="sxs-lookup"><span data-stu-id="a07a7-108">[out] The runtime type.</span></span> <span data-ttu-id="a07a7-109">此參數會傳回適用于 CLR 桌上出版本的 `COR_PRF_DESKTOP_CLR`，或用於 Silverlight 中所使用之 CLR 核心版本的 `COR_PRF_CORE_CLR`。</span><span class="sxs-lookup"><span data-stu-id="a07a7-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="a07a7-110">脫銷CLR 的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a07a7-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="a07a7-111">脫銷CLR 的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a07a7-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="a07a7-112">脫銷CLR 的組建版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a07a7-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="a07a7-113">脫銷與軟體更新相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a07a7-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="a07a7-114">在`szVersionString` 指向之緩衝區的長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="a07a7-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="a07a7-115">脫銷`szVersionString`的長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="a07a7-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="a07a7-116">脫銷CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="a07a7-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a07a7-117">備註</span><span class="sxs-lookup"><span data-stu-id="a07a7-117">Remarks</span></span>  
 <span data-ttu-id="a07a7-118">您可以為任何參數傳遞 null。</span><span class="sxs-lookup"><span data-stu-id="a07a7-118">You may pass null for any parameter.</span></span> <span data-ttu-id="a07a7-119">不過，除非 `szVersionString` 也是 null，否則 `pcchVersionString` 不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="a07a7-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a07a7-120">需求</span><span class="sxs-lookup"><span data-stu-id="a07a7-120">Requirements</span></span>  
 <span data-ttu-id="a07a7-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a07a7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a07a7-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a07a7-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a07a7-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a07a7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a07a7-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a07a7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07a7-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="a07a7-125">See also</span></span>

- [<span data-ttu-id="a07a7-126">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="a07a7-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a07a7-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="a07a7-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a07a7-128">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="a07a7-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
