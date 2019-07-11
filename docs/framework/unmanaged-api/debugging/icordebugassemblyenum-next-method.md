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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00adc852a0940766cdd4188ffa5d6be2b472e51f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744885"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="e906a-102">ICorDebugAssemblyEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="e906a-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="e906a-103">從集合中，從目前游標位置開始，取得指定的組件數目。</span><span class="sxs-lookup"><span data-stu-id="e906a-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e906a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e906a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e906a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e906a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e906a-106">[in]要擷取的組件數目。</span><span class="sxs-lookup"><span data-stu-id="e906a-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e906a-107">[out]指標的陣列，其中每一個指向 ICorDebugAssembly 物件，表示組件。</span><span class="sxs-lookup"><span data-stu-id="e906a-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e906a-108">[out]實際傳回的組件數目指標。</span><span class="sxs-lookup"><span data-stu-id="e906a-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="e906a-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="e906a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e906a-110">需求</span><span class="sxs-lookup"><span data-stu-id="e906a-110">Requirements</span></span>  
 <span data-ttu-id="e906a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e906a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e906a-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e906a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e906a-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e906a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e906a-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e906a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
