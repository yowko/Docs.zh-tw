---
title: "ICorDebugController::IsRunning 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.IsRunning
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0cfb2c0fe3c2ebf9473afc4f1a93f50e8fe437f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="a228e-102">ICorDebugController::IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="a228e-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="a228e-103">取得值，指出是否在處理程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="a228e-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a228e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a228e-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a228e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a228e-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="a228e-106">[out]值的指標`true`程序中的執行緒執行自由; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="a228e-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a228e-107">需求</span><span class="sxs-lookup"><span data-stu-id="a228e-107">Requirements</span></span>  
 <span data-ttu-id="a228e-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a228e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a228e-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a228e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a228e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a228e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a228e-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a228e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a228e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a228e-112">See Also</span></span>  
 
