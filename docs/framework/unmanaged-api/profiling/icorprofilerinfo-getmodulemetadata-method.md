---
title: ICorProfilerInfo::GetModuleMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 74df0fb412e7fb3d9f779391ec84f07a0379a2cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724113"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="5dd2e-102">ICorProfilerInfo::GetModuleMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="5dd2e-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>

<span data-ttu-id="5dd2e-103">取得對應至指定模組的中繼資料介面實例。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dd2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dd2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dd2e-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="5dd2e-106">在介面實例將對應之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5dd2e-107">在 [CorOpenFlags](../metadata/coropenflags-enumeration.md) 列舉的值，指定開啟資訊清單檔案的模式。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="5dd2e-108">只有 `ofRead` 、 `ofWrite` 和 `ofNoTransform` 位有效。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="5dd2e-109">在將抓取其實例的中繼資料介面 (GUID) 的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="5dd2e-110">請參閱介面清單的 [中繼資料介面](../metadata/metadata-interfaces.md) 。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="5dd2e-111">擴展中繼資料介面實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd2e-112">備註</span><span class="sxs-lookup"><span data-stu-id="5dd2e-112">Remarks</span></span>  

 <span data-ttu-id="5dd2e-113">您可能會要求以讀取/寫入模式開啟中繼資料，但這會導致程式的較慢中繼資料執行，因為對中繼資料所做的變更無法從編譯器進行優化。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="5dd2e-114">某些模組 (例如資源模組) 沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="5dd2e-115">在這些情況下， `GetModuleMetaData` 將會傳回 S_FALSE 的 HRESULT 值，並傳回 \* 中的 null `ppOut` 。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd2e-116">需求</span><span class="sxs-lookup"><span data-stu-id="5dd2e-116">Requirements</span></span>  

 <span data-ttu-id="5dd2e-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dd2e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd2e-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5dd2e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5dd2e-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dd2e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dd2e-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dd2e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd2e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dd2e-121">See also</span></span>

- [<span data-ttu-id="5dd2e-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5dd2e-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
