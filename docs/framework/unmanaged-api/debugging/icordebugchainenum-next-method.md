---
title: ICorDebugChainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 0f42020821ec71d1e59ae8097f22ee530e16a576
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706173"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="ceeb6-102">ICorDebugChainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="ceeb6-102">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="ceeb6-103">從目前位置開始，取得列舉中指定的 ICorDebugChain 實例數目。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceeb6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ceeb6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceeb6-105">參數</span><span class="sxs-lookup"><span data-stu-id="ceeb6-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ceeb6-106">在 `ICorDebugChain` 要取出的實例數目。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="ceeb6-107">擴展指標的陣列，每個指標 `ICorDebugChain` 都會指向代表一個鏈的物件。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ceeb6-108">擴展實際傳回之實例數目的指標 `ICorDebugChain` 。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="ceeb6-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceeb6-110">需求</span><span class="sxs-lookup"><span data-stu-id="ceeb6-110">Requirements</span></span>  

 <span data-ttu-id="ceeb6-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ceeb6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceeb6-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceeb6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceeb6-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceeb6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceeb6-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceeb6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
