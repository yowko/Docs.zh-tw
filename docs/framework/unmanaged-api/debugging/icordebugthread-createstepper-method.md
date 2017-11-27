---
title: "ICorDebugThread::CreateStepper 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="4d1f0-102">ICorDebugThread::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="4d1f0-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="4d1f0-103">建立可讓您逐步執行此 ICorDebugThread 的使用中框架的 ICorDebugStepper 物件。</span><span class="sxs-lookup"><span data-stu-id="4d1f0-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d1f0-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d1f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d1f0-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="4d1f0-106">[out]位址指標`ICorDebugStepper`物件，可讓您逐步執行此執行緒的作用中框架。</span><span class="sxs-lookup"><span data-stu-id="4d1f0-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d1f0-107">備註</span><span class="sxs-lookup"><span data-stu-id="4d1f0-107">Remarks</span></span>  
 <span data-ttu-id="4d1f0-108">使用中畫面格可能是 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d1f0-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="4d1f0-109">`ICorDebugStepper`介面必須用來執行實際的逐步執行。</span><span class="sxs-lookup"><span data-stu-id="4d1f0-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1f0-110">需求</span><span class="sxs-lookup"><span data-stu-id="4d1f0-110">Requirements</span></span>  
 <span data-ttu-id="4d1f0-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d1f0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d1f0-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d1f0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d1f0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d1f0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d1f0-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d1f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
