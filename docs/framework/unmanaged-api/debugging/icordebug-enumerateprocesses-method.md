---
title: "ICorDebug::EnumerateProcesses 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffabcc97a4af33fc859cd096e671f98d52e89e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="aed17-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="aed17-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="aed17-103">取得正在進行偵錯的處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aed17-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed17-104">語法</span><span class="sxs-lookup"><span data-stu-id="aed17-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aed17-105">參數</span><span class="sxs-lookup"><span data-stu-id="aed17-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="aed17-106">ICorDebugProcessEnum 物件的列舉程式進行偵錯的處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="aed17-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aed17-107">需求</span><span class="sxs-lookup"><span data-stu-id="aed17-107">Requirements</span></span>  
 <span data-ttu-id="aed17-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aed17-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aed17-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aed17-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aed17-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aed17-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aed17-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed17-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="aed17-112">See Also</span></span>  
 [<span data-ttu-id="aed17-113">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="aed17-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
