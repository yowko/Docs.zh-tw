---
title: ICorDebugAssemblyEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: 155354b335caf83c466c8d9d6711f36c7efc9298
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894804"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="bd987-102">ICorDebugAssemblyEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="bd987-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="bd987-103">從目前的資料指標位置開始，取得集合中指定的元件數目。</span><span class="sxs-lookup"><span data-stu-id="bd987-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd987-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd987-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd987-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd987-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bd987-106">在要抓取的元件數目。</span><span class="sxs-lookup"><span data-stu-id="bd987-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="bd987-107">脫銷指標陣列，其中每一個都會指向代表元件的 ICorDebugAssembly 物件。</span><span class="sxs-lookup"><span data-stu-id="bd987-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bd987-108">脫銷實際傳回之元件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="bd987-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="bd987-109">如果`celt`是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="bd987-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd987-110">需求</span><span class="sxs-lookup"><span data-stu-id="bd987-110">Requirements</span></span>  
 <span data-ttu-id="bd987-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd987-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd987-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd987-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd987-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd987-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd987-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd987-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
