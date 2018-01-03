---
title: "ICorDebugProcess::GetHandle 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28065bff38fdf8c7f69920be1f7c6704dd03d69d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="9a988-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="9a988-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="9a988-103">取得處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9a988-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a988-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a988-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a988-105">參數</span><span class="sxs-lookup"><span data-stu-id="9a988-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="9a988-106">[out]指標`HPROCESS`也就是處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9a988-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a988-107">備註</span><span class="sxs-lookup"><span data-stu-id="9a988-107">Remarks</span></span>  
 <span data-ttu-id="9a988-108">擷取控制代碼的擁有者偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="9a988-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="9a988-109">偵錯工具應該重複的控制代碼後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="9a988-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a988-110">需求</span><span class="sxs-lookup"><span data-stu-id="9a988-110">Requirements</span></span>  
 <span data-ttu-id="9a988-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a988-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a988-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a988-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a988-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a988-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a988-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a988-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
