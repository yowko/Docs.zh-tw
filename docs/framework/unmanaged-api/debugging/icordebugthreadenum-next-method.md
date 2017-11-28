---
title: "ICorDebugThreadEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThreadEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb26dd4cd625c025685113611a189b51a4d56a99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="29926-102">ICorDebugThreadEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="29926-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="29926-103">從列舉型別，從目前位置開始，取得指定 ICorDebugThread 執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="29926-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29926-104">語法</span><span class="sxs-lookup"><span data-stu-id="29926-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29926-105">參數</span><span class="sxs-lookup"><span data-stu-id="29926-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="29926-106">[in]數目`ICorDebugThread`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29926-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="29926-107">[out]陣列的指標，其中每個指向`ICorDebugThread`代表執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="29926-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="29926-108">[out]指標的數目`ICorDebugThread`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29926-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="29926-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="29926-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29926-110">需求</span><span class="sxs-lookup"><span data-stu-id="29926-110">Requirements</span></span>  
 <span data-ttu-id="29926-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29926-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29926-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29926-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29926-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29926-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29926-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29926-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
