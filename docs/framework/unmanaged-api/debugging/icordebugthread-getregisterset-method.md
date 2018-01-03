---
title: "ICorDebugThread::GetRegisterSet 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3eb4acd546a2a87f7844a442110dc15343cc218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="46f57-102">ICorDebugThread::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="46f57-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="46f57-103">取得為這個 ICorDebugThread 物件的使用中部分相關聯的登錄設定的介面指標。</span><span class="sxs-lookup"><span data-stu-id="46f57-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f57-104">語法</span><span class="sxs-lookup"><span data-stu-id="46f57-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46f57-105">參數</span><span class="sxs-lookup"><span data-stu-id="46f57-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="46f57-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)介面物件，表示登錄設定這個執行緒的使用中部分。</span><span class="sxs-lookup"><span data-stu-id="46f57-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f57-107">需求</span><span class="sxs-lookup"><span data-stu-id="46f57-107">Requirements</span></span>  
 <span data-ttu-id="46f57-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46f57-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f57-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46f57-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46f57-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46f57-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46f57-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f57-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
