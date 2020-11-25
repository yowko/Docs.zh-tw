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
ms.openlocfilehash: fdb2b1601e0164de19bcc1e8f60856346aeaacb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698009"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="26b33-102">ICorProfilerInfo3::GetRuntimeInformation 方法</span><span class="sxs-lookup"><span data-stu-id="26b33-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>

<span data-ttu-id="26b33-103">提供所分析之 common language runtime (CLR) 的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="26b33-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b33-104">語法</span><span class="sxs-lookup"><span data-stu-id="26b33-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="26b33-105">參數</span><span class="sxs-lookup"><span data-stu-id="26b33-105">Parameters</span></span>  

 `pClrInstanceId`  
 <span data-ttu-id="26b33-106">擴展進程中執行中 CLR 實例的代表性識別碼。</span><span class="sxs-lookup"><span data-stu-id="26b33-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="26b33-107">這與 `ClrInstanceID` Windows 事件追蹤 (ETW) 啟動事件報表相同。</span><span class="sxs-lookup"><span data-stu-id="26b33-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="26b33-108">擴展執行時間型別。</span><span class="sxs-lookup"><span data-stu-id="26b33-108">[out] The runtime type.</span></span> <span data-ttu-id="26b33-109">此參數會 `COR_PRF_DESKTOP_CLR` 針對適用于 clr 的桌上出版本，或用於 `COR_PRF_CORE_CLR` Silverlight 中所使用之 clr 的核心版本傳回。</span><span class="sxs-lookup"><span data-stu-id="26b33-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="26b33-110">擴展CLR 的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="26b33-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="26b33-111">擴展CLR 的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="26b33-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="26b33-112">擴展CLR 的組建版本號碼。</span><span class="sxs-lookup"><span data-stu-id="26b33-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="26b33-113">擴展與軟體更新相關聯之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="26b33-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="26b33-114">在指向之緩衝區的長度（以字元為單位） `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="26b33-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="26b33-115">擴展的長度（以字元為單位） `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="26b33-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="26b33-116">擴展CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="26b33-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b33-117">備註</span><span class="sxs-lookup"><span data-stu-id="26b33-117">Remarks</span></span>  

 <span data-ttu-id="26b33-118">您可以針對任何參數傳遞 null。</span><span class="sxs-lookup"><span data-stu-id="26b33-118">You may pass null for any parameter.</span></span> <span data-ttu-id="26b33-119">不過， `pcchVersionString` 除非也是 null，否則不可以是 null `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="26b33-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b33-120">需求</span><span class="sxs-lookup"><span data-stu-id="26b33-120">Requirements</span></span>  

 <span data-ttu-id="26b33-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26b33-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b33-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26b33-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26b33-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b33-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b33-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b33-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b33-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26b33-125">See also</span></span>

- [<span data-ttu-id="26b33-126">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="26b33-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="26b33-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="26b33-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="26b33-128">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="26b33-128">Profiling</span></span>](index.md)
