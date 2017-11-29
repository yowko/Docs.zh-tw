---
title: "ICorProfilerInfo::GetModuleMetaData 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleMetaData
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 540ed6f1f84f096563aa94798090c3511d6db5d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="f5b74-102">ICorProfilerInfo::GetModuleMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="f5b74-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="f5b74-103">取得對應至指定的模組的中繼資料介面執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5b74-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b74-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5b74-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5b74-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5b74-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f5b74-106">[in]對應介面的執行個體的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="f5b74-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="f5b74-107">[in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉，指定開啟資訊清單檔案的模式。</span><span class="sxs-lookup"><span data-stu-id="f5b74-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="f5b74-108">只有`ofRead`，`ofWrite`和`ofNoTransform`個位元都是有效。</span><span class="sxs-lookup"><span data-stu-id="f5b74-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="f5b74-109">[in]參考識別碼 (GUID) 會擷取其執行個體的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="f5b74-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="f5b74-110">請參閱[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)的介面清單。</span><span class="sxs-lookup"><span data-stu-id="f5b74-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="f5b74-111">[out]中繼資料介面執行個體的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f5b74-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5b74-112">備註</span><span class="sxs-lookup"><span data-stu-id="f5b74-112">Remarks</span></span>  
 <span data-ttu-id="f5b74-113">您可能會在讀取/寫入模式中開啟中繼資料要求，但是這樣會導致程式的中繼資料執行速度緩慢，編譯器所顯示的一樣，因為變更無法最佳化中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f5b74-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="f5b74-114">某些模組 （例如資源模組） 會有任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f5b74-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="f5b74-115">在這些情況下，`GetModuleMetaData`會傳回 S_FALSE 和中的 null 的 HRESULT 值 *`ppOut`。</span><span class="sxs-lookup"><span data-stu-id="f5b74-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in *`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b74-116">需求</span><span class="sxs-lookup"><span data-stu-id="f5b74-116">Requirements</span></span>  
 <span data-ttu-id="f5b74-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b74-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b74-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5b74-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5b74-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5b74-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5b74-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b74-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b74-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b74-121">See Also</span></span>  
 [<span data-ttu-id="f5b74-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f5b74-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
