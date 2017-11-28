---
title: "ICorDebugMDA::GetFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1388356cb3c67c1a4b292931710dc72323ed6da8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="ebef5-102">ICorDebugMDA::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="ebef5-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="ebef5-103">取得由 managed 偵錯助理 (MDA) 相關聯的旗標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="ebef5-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebef5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebef5-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebef5-105">參數</span><span class="sxs-lookup"><span data-stu-id="ebef5-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="ebef5-106">[in]位元組合[CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)列舉值，指定這個 MDA 的旗標的設定。</span><span class="sxs-lookup"><span data-stu-id="ebef5-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebef5-107">需求</span><span class="sxs-lookup"><span data-stu-id="ebef5-107">Requirements</span></span>  
 <span data-ttu-id="ebef5-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebef5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebef5-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebef5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebef5-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebef5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebef5-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebef5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebef5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebef5-112">See Also</span></span>  
 [<span data-ttu-id="ebef5-113">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="ebef5-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="ebef5-114">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="ebef5-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
