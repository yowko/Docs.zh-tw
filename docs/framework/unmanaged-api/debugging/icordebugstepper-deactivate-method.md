---
title: "ICorDebugStepper::Deactivate 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Deactivate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 056d60a56c37126163361166e16da5d7949e2dbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="f2f69-102">ICorDebugStepper::Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="f2f69-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="f2f69-103">會導致此 ICorDebugStepper 取消它所收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="f2f69-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f69-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2f69-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f2f69-105">備註</span><span class="sxs-lookup"><span data-stu-id="f2f69-105">Remarks</span></span>  
 <span data-ttu-id="f2f69-106">已取消最近收到的步驟命令之後發出新的逐步執行指令。</span><span class="sxs-lookup"><span data-stu-id="f2f69-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f69-107">需求</span><span class="sxs-lookup"><span data-stu-id="f2f69-107">Requirements</span></span>  
 <span data-ttu-id="f2f69-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f69-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2f69-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2f69-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f69-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f69-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
