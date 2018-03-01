---
title: "ICorDebugEval::GetThread 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a2ed99c2a939d2b39f6b236165b79634f2fc2c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="a60e0-102">ICorDebugEval::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="a60e0-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="a60e0-103">取得這項評估在執行或是將執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a60e0-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a60e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a60e0-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a60e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a60e0-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="a60e0-106">[out]ICorDebugThread 物件，表示執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a60e0-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a60e0-107">需求</span><span class="sxs-lookup"><span data-stu-id="a60e0-107">Requirements</span></span>  
 <span data-ttu-id="a60e0-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a60e0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a60e0-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a60e0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a60e0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a60e0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a60e0-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a60e0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
