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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d02a68e80e34be906e9fe09f3457a0f2214c6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405063"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="6d8c0-102">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="6d8c0-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="6d8c0-103">取得這個呼叫鏈結發生的原因。</span><span class="sxs-lookup"><span data-stu-id="6d8c0-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d8c0-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d8c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d8c0-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="6d8c0-106">[out]CorDebugChainReason 列舉，指出此呼叫鏈結的發生原因的值 （位元的組合） 的指標。</span><span class="sxs-lookup"><span data-stu-id="6d8c0-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d8c0-107">需求</span><span class="sxs-lookup"><span data-stu-id="6d8c0-107">Requirements</span></span>  
 <span data-ttu-id="6d8c0-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d8c0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8c0-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d8c0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d8c0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d8c0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d8c0-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8c0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
