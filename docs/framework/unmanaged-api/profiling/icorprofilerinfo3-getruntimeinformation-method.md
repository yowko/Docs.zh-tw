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
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496395"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="2c53e-102">ICorProfilerInfo3::GetRuntimeInformation 方法</span><span class="sxs-lookup"><span data-stu-id="2c53e-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="2c53e-103">提供所分析之 common language runtime （CLR）的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="2c53e-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c53e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c53e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2c53e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c53e-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="2c53e-106">脫銷進程中執行中 CLR 實例的代表識別碼。</span><span class="sxs-lookup"><span data-stu-id="2c53e-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="2c53e-107">這與 `ClrInstanceID` Windows 事件追蹤（ETW）啟動附隨報告的相同。</span><span class="sxs-lookup"><span data-stu-id="2c53e-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="2c53e-108">脫銷執行時間類型。</span><span class="sxs-lookup"><span data-stu-id="2c53e-108">[out] The runtime type.</span></span> <span data-ttu-id="2c53e-109">這個參數會 `COR_PRF_DESKTOP_CLR` 針對 clr 的桌上出版本或 `COR_PRF_CORE_CLR` Silverlight 中使用的 clr 核心版本傳回。</span><span class="sxs-lookup"><span data-stu-id="2c53e-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="2c53e-110">脫銷CLR 的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2c53e-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="2c53e-111">脫銷CLR 的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2c53e-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="2c53e-112">脫銷CLR 的組建版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2c53e-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="2c53e-113">脫銷與軟體更新相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2c53e-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="2c53e-114">在指向之緩衝區的長度（以字元為單位） `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="2c53e-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="2c53e-115">脫銷的長度（以字元為單位） `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="2c53e-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="2c53e-116">脫銷CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="2c53e-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c53e-117">備註</span><span class="sxs-lookup"><span data-stu-id="2c53e-117">Remarks</span></span>  
 <span data-ttu-id="2c53e-118">您可以為任何參數傳遞 null。</span><span class="sxs-lookup"><span data-stu-id="2c53e-118">You may pass null for any parameter.</span></span> <span data-ttu-id="2c53e-119">不過， `pcchVersionString` 除非也是 null，否則不可以是 null `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="2c53e-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c53e-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="2c53e-120">Requirements</span></span>  
 <span data-ttu-id="2c53e-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c53e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c53e-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c53e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c53e-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c53e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c53e-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c53e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c53e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c53e-125">See also</span></span>

- [<span data-ttu-id="2c53e-126">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="2c53e-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2c53e-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="2c53e-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2c53e-128">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="2c53e-128">Profiling</span></span>](index.md)
