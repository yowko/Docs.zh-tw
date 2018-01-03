---
title: "ICorDebugChain::GetReason 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c23385c0d7b6173659e071735dee5d2d75a9e33a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="f253f-102">ICorDebugChain::GetReason 方法</span><span class="sxs-lookup"><span data-stu-id="f253f-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="f253f-103">取得這個呼叫鏈結發生的原因。</span><span class="sxs-lookup"><span data-stu-id="f253f-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f253f-104">語法</span><span class="sxs-lookup"><span data-stu-id="f253f-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f253f-105">參數</span><span class="sxs-lookup"><span data-stu-id="f253f-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="f253f-106">[out]CorDebugChainReason 列舉，指出此呼叫鏈結的發生原因的值 （位元的組合） 的指標。</span><span class="sxs-lookup"><span data-stu-id="f253f-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f253f-107">需求</span><span class="sxs-lookup"><span data-stu-id="f253f-107">Requirements</span></span>  
 <span data-ttu-id="f253f-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f253f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f253f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f253f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f253f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f253f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f253f-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f253f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
