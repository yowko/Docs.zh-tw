---
title: ICorDebugChain::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: cfe884c3d26e7a52618eb9945f0af9a167132f05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724373"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="ef8f8-102">ICorDebugChain::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="ef8f8-102">ICorDebugChain::IsManaged Method</span></span>

<span data-ttu-id="ef8f8-103">取得值，這個值表示此鏈是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef8f8-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef8f8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef8f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef8f8-105">Parameters</span></span>  

 `pManaged`  
 <span data-ttu-id="ef8f8-106">[out] `true` 如果此鏈正在執行 managed 程式碼，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ef8f8-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8f8-107">需求</span><span class="sxs-lookup"><span data-stu-id="ef8f8-107">Requirements</span></span>  

 <span data-ttu-id="ef8f8-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef8f8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8f8-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef8f8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef8f8-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef8f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef8f8-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
