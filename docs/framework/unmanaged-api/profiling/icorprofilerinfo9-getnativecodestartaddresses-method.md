---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ca1643dfa980fa647164accf6432082428124acb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541235"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="d93aa-102">ICorProfilerInfo9：： GetNativeCodeStartAddresses 方法</span><span class="sxs-lookup"><span data-stu-id="d93aa-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="d93aa-103">在指定 functionId 和 rejitId 的情況下，列舉此程式碼目前存在的所有可編譯版本的機器碼開始位址。</span><span class="sxs-lookup"><span data-stu-id="d93aa-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="d93aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="d93aa-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="d93aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="d93aa-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="d93aa-106">\[in] 應傳回其原生程式碼起始位址的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="d93aa-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="d93aa-107">\[in] JIT 重新編譯函式的識別。</span><span class="sxs-lookup"><span data-stu-id="d93aa-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="d93aa-108">\[in] 陣列的大小上限 `codeStartAddresses` 。</span><span class="sxs-lookup"><span data-stu-id="d93aa-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="d93aa-109">\[out] 可用的位址數目。</span><span class="sxs-lookup"><span data-stu-id="d93aa-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="d93aa-110">\[out）的陣列 `UINT_PTR` ，其中每一個都是指定之函式之原生主體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="d93aa-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="d93aa-111">備註</span><span class="sxs-lookup"><span data-stu-id="d93aa-111">Remarks</span></span>

<span data-ttu-id="d93aa-112">啟用分層式編譯時，函式可能會有一個以上的機器碼主體。</span><span class="sxs-lookup"><span data-stu-id="d93aa-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="d93aa-113">需求</span><span class="sxs-lookup"><span data-stu-id="d93aa-113">Requirements</span></span>

<span data-ttu-id="d93aa-114">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="d93aa-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="d93aa-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d93aa-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d93aa-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d93aa-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d93aa-117">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d93aa-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d93aa-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d93aa-118">See also</span></span>

- [<span data-ttu-id="d93aa-119">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="d93aa-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
