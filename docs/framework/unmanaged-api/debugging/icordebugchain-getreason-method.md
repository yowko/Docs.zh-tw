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
ms.openlocfilehash: e51ee2e4d44af547c82a21a782121976d07118c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124721"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="4dbd4-102">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="4dbd4-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="4dbd4-103">取得此呼叫鏈的創世原因。</span><span class="sxs-lookup"><span data-stu-id="4dbd4-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dbd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="4dbd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dbd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="4dbd4-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="4dbd4-106">脫銷CorDebugChainReason 列舉的值指標，指出這個呼叫鏈的創世原因。（位合）。</span><span class="sxs-lookup"><span data-stu-id="4dbd4-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dbd4-107">需求</span><span class="sxs-lookup"><span data-stu-id="4dbd4-107">Requirements</span></span>  
 <span data-ttu-id="4dbd4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4dbd4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dbd4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dbd4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dbd4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dbd4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dbd4-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dbd4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
