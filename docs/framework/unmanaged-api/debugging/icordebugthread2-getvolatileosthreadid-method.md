---
title: "ICorDebugThread2::GetVolatileOSThreadID 方法"
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
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd15407e0e2866cf7b177c936b172d06ba76d83b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="9b33a-102">ICorDebugThread2::GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="9b33a-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="9b33a-103">取得此 ICorDebugThread2 作業系統執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="9b33a-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b33a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b33a-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b33a-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b33a-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="9b33a-106">[out]這個執行緒的作業系統執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="9b33a-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b33a-107">需求</span><span class="sxs-lookup"><span data-stu-id="9b33a-107">Requirements</span></span>  
 <span data-ttu-id="9b33a-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b33a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b33a-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b33a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b33a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b33a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b33a-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b33a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
