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
ms.openlocfilehash: 9b5059d9e4bf9b79dc67664c7a7971041d1cf35b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861680"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="daade-102">ICorProfilerInfo8：： GetDynamicFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="daade-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="daade-103">抓取動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="daade-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="daade-104">語法</span><span class="sxs-lookup"><span data-stu-id="daade-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="daade-105">參數</span><span class="sxs-lookup"><span data-stu-id="daade-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="daade-106">在中 \[] 要取得其資訊的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="daade-106">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="daade-107">\[in]：定義函式之父類別所在模組的指標。</span><span class="sxs-lookup"><span data-stu-id="daade-107">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="daade-108">\[out] 函式簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="daade-108">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="daade-109">\[out] 函式簽章的位元組計數指標。</span><span class="sxs-lookup"><span data-stu-id="daade-109">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="daade-110">\[in] `wszName` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="daade-110">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="daade-111">\[out] `wszName` 陣列中的字元數。</span><span class="sxs-lookup"><span data-stu-id="daade-111">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="daade-112">\[out] `WCHAR` 的陣列，這是函式的名稱（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="daade-112">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="daade-113">備註</span><span class="sxs-lookup"><span data-stu-id="daade-113">Remarks</span></span>

<span data-ttu-id="daade-114">某些方法（例如 IL Stub 或 LCG）沒有相關聯的中繼資料可使用[IMetaDataImport](../metadata/imetadataimport-interface.md)和[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api 來抓取。</span><span class="sxs-lookup"><span data-stu-id="daade-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="daade-115">分析工具可以透過指令指標或接聽[ICorProfilerCallback8：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來遇到這類方法。</span><span class="sxs-lookup"><span data-stu-id="daade-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="daade-116">此 API 可用於抓取動態方法的相關資訊，包括易記名稱（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="daade-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="daade-117">需求</span><span class="sxs-lookup"><span data-stu-id="daade-117">Requirements</span></span>

<span data-ttu-id="daade-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daade-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="daade-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="daade-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="daade-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daade-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="daade-121">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="daade-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="daade-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="daade-122">See also</span></span>

- [<span data-ttu-id="daade-123">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="daade-123">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
