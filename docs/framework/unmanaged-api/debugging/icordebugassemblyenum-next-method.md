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
ms.openlocfilehash: dd915a82551f5bed688a28ab77f5d6cf4e38af0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719244"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="d07e3-102">ICorDebugAssemblyEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="d07e3-102">ICorDebugAssemblyEnum::Next Method</span></span>

<span data-ttu-id="d07e3-103">從目前的資料指標位置開始，取得集合中指定的元件數目。</span><span class="sxs-lookup"><span data-stu-id="d07e3-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d07e3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d07e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d07e3-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d07e3-106">在要取出的元件數目。</span><span class="sxs-lookup"><span data-stu-id="d07e3-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d07e3-107">擴展指標的陣列，每個指標都會指向代表元件的 ICorDebugAssembly 物件。</span><span class="sxs-lookup"><span data-stu-id="d07e3-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d07e3-108">擴展實際傳回的元件數目指標。</span><span class="sxs-lookup"><span data-stu-id="d07e3-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="d07e3-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="d07e3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d07e3-110">需求</span><span class="sxs-lookup"><span data-stu-id="d07e3-110">Requirements</span></span>  

 <span data-ttu-id="d07e3-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d07e3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d07e3-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d07e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d07e3-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d07e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d07e3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d07e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
