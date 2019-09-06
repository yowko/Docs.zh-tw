---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 45a40d49cea2dd5f881fbd47cc2fb4bd96e8f9ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243990"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="06561-102">ICorProfilerInfo8:: GetDynamicFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="06561-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="06561-103">抓取動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="06561-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="06561-104">語法</span><span class="sxs-lookup"><span data-stu-id="06561-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a><span data-ttu-id="06561-105">參數</span><span class="sxs-lookup"><span data-stu-id="06561-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="06561-106">在要取得其資訊之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="06561-106">[in] The ID of the function for which to retrieve information.</span></span>

`moduleId` \
<span data-ttu-id="06561-107">在定義函式之父類別所在模組的指標。</span><span class="sxs-lookup"><span data-stu-id="06561-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>

`ppvSig` \
<span data-ttu-id="06561-108">脫銷函數簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="06561-108">[out] A pointer to the signature for the function.</span></span>

`pbSig` \
<span data-ttu-id="06561-109">脫銷函數簽章的位元組計數指標。</span><span class="sxs-lookup"><span data-stu-id="06561-109">[out] A pointer to the count of bytes for the function signature.</span></span>

`cchName` \
<span data-ttu-id="06561-110">[in] `wszName` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="06561-110">[in] The maximum size of the `wszName` array.</span></span>

`pcchName` \
<span data-ttu-id="06561-111">脫銷`wszName`陣列中的字元數。</span><span class="sxs-lookup"><span data-stu-id="06561-111">[out] The number of characters in the `wszName` array.</span></span>

`wszName` \
<span data-ttu-id="06561-112">脫銷陣列`WCHAR` , 這是函式的名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="06561-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="06561-113">備註</span><span class="sxs-lookup"><span data-stu-id="06561-113">Remarks</span></span>

<span data-ttu-id="06561-114">某些方法 (例如 IL Stub 或 LCG) 沒有相關聯的中繼資料可使用[IMetaDataImport](../metadata/imetadataimport-interface.md)和[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api 來抓取。</span><span class="sxs-lookup"><span data-stu-id="06561-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="06561-115">分析工具可以透過指令指標或接聽[ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md), 來遇到這類方法。</span><span class="sxs-lookup"><span data-stu-id="06561-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="06561-116">此 API 可用於抓取動態方法的相關資訊, 包括易記名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="06561-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="06561-117">需求</span><span class="sxs-lookup"><span data-stu-id="06561-117">Requirements</span></span>

<span data-ttu-id="06561-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06561-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="06561-119">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="06561-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="06561-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06561-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="06561-121">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06561-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="06561-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06561-122">See also</span></span>

- [<span data-ttu-id="06561-123">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="06561-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
