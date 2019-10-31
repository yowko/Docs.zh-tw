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
ms.openlocfilehash: 86fa44b609b4b89cfaa28f0bfa7bbdce6217623f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122862"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="f8397-102">ICorDebugAssemblyEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="f8397-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="f8397-103">從目前的資料指標位置開始，取得集合中指定的元件數目。</span><span class="sxs-lookup"><span data-stu-id="f8397-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8397-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8397-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8397-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8397-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f8397-106">在要抓取的元件數目。</span><span class="sxs-lookup"><span data-stu-id="f8397-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f8397-107">脫銷指標陣列，其中每一個都會指向代表元件的 ICorDebugAssembly 物件。</span><span class="sxs-lookup"><span data-stu-id="f8397-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f8397-108">脫銷實際傳回之元件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="f8397-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="f8397-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="f8397-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8397-110">需求</span><span class="sxs-lookup"><span data-stu-id="f8397-110">Requirements</span></span>  
 <span data-ttu-id="f8397-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8397-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8397-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8397-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8397-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8397-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8397-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8397-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
