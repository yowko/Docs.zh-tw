---
title: "ICorDebugChainEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3d6d587b1a249d08ffb250453fb9c007dc3df3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="8471e-102">ICorDebugChainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="8471e-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="8471e-103">取得 ICorDebugChain 執行個體的指定的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="8471e-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8471e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8471e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8471e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8471e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8471e-106">[in]數目`ICorDebugChain`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8471e-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="8471e-107">[out]陣列的指標，其中每個指向`ICorDebugChain`物件，代表鏈結。</span><span class="sxs-lookup"><span data-stu-id="8471e-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8471e-108">[out]數目的指標`ICorDebugChain`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8471e-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="8471e-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="8471e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8471e-110">需求</span><span class="sxs-lookup"><span data-stu-id="8471e-110">Requirements</span></span>  
 <span data-ttu-id="8471e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8471e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8471e-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8471e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8471e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8471e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8471e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8471e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
