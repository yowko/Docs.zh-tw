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
ms.openlocfilehash: 58e40995012d98c1af6a41eb12d898c6b9b1d47b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719667"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="6e56b-102">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="6e56b-102">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="6e56b-103">取得此呼叫鏈創世的原因。</span><span class="sxs-lookup"><span data-stu-id="6e56b-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e56b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e56b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e56b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e56b-105">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="6e56b-106">擴展值的指標， (CorDebugChainReason 列舉的位元組合) ，指出這個呼叫鏈的創世原因。</span><span class="sxs-lookup"><span data-stu-id="6e56b-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e56b-107">需求</span><span class="sxs-lookup"><span data-stu-id="6e56b-107">Requirements</span></span>  

 <span data-ttu-id="6e56b-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e56b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e56b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e56b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e56b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e56b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e56b-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e56b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
