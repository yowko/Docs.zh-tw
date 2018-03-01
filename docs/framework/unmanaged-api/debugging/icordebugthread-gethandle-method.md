---
title: "ICorDebugThread::GetHandle 方法"
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
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7a932d04fef438e19176af565c92e0673339e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="837ca-102">ICorDebugThread::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="837ca-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="837ca-103">取得此 ICorDebugThread 的使用中部分目前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="837ca-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="837ca-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="837ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="837ca-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="837ca-106">[out]這個執行緒的使用中部分的控制代碼 HTHREAD 指標。</span><span class="sxs-lookup"><span data-stu-id="837ca-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837ca-107">備註</span><span class="sxs-lookup"><span data-stu-id="837ca-107">Remarks</span></span>  
 <span data-ttu-id="837ca-108">處理程序會執行，而且可能會不同執行緒的不同部分可能會變更控制代碼。</span><span class="sxs-lookup"><span data-stu-id="837ca-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="837ca-109">這個控制代碼是由偵錯 API 所擁有。</span><span class="sxs-lookup"><span data-stu-id="837ca-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="837ca-110">偵錯工具應該使用之前，先複製它。</span><span class="sxs-lookup"><span data-stu-id="837ca-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837ca-111">需求</span><span class="sxs-lookup"><span data-stu-id="837ca-111">Requirements</span></span>  
 <span data-ttu-id="837ca-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="837ca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837ca-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="837ca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="837ca-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="837ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="837ca-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
