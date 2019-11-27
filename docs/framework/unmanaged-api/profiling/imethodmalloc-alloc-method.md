---
title: IMethodMalloc::Alloc 方法
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447562"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="be098-102">IMethodMalloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="be098-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="be098-103">嘗試為新的 Microsoft 中繼語言（MSIL）函數主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="be098-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="be098-104">語法</span><span class="sxs-lookup"><span data-stu-id="be098-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="be098-105">參數</span><span class="sxs-lookup"><span data-stu-id="be098-105">Parameters</span></span>

`cb`\
<span data-ttu-id="be098-106">在要配置給方法主體的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="be098-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="be098-107">備註</span><span class="sxs-lookup"><span data-stu-id="be098-107">Remarks</span></span>

 <span data-ttu-id="be098-108">配置的記憶體會從大於與此配置器相關聯之模組基底位址的位址開始。</span><span class="sxs-lookup"><span data-stu-id="be098-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="be098-109">換句話說，每個配置器都會針對特定模組建立，並會嘗試在其基底位址的正位移上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="be098-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="be098-110">如果 `Alloc` 無法在大於模組基底位址的位址上配置所要求的位元組數目，則會傳回 E_OUTOFMEMORY，而不論實際的記憶體空間量是否可用。</span><span class="sxs-lookup"><span data-stu-id="be098-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="be098-111">`Alloc` 的方法應該與[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="be098-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="be098-112">需求</span><span class="sxs-lookup"><span data-stu-id="be098-112">Requirements</span></span>
 <span data-ttu-id="be098-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be098-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="be098-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be098-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="be098-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be098-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="be098-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be098-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="be098-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be098-117">See also</span></span>

- [<span data-ttu-id="be098-118">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="be098-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
