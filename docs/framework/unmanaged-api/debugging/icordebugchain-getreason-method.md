---
title: ICorDebugChain::GetReason 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 94672c88864efc431acde8f29e406f4fbbc644ee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894551"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="a8ead-102">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="a8ead-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="a8ead-103">取得此呼叫鏈的創世原因。</span><span class="sxs-lookup"><span data-stu-id="a8ead-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ead-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8ead-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ead-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8ead-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="a8ead-106">脫銷CorDebugChainReason 列舉的值指標，指出這個呼叫鏈的創世原因。（位合）。</span><span class="sxs-lookup"><span data-stu-id="a8ead-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ead-107">需求</span><span class="sxs-lookup"><span data-stu-id="a8ead-107">Requirements</span></span>  
 <span data-ttu-id="a8ead-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ead-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ead-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8ead-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8ead-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8ead-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8ead-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ead-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
