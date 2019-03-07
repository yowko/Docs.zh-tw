---
title: ICorDebugProcess::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d81564a34ed8e7ef75840e3a174661c36f5411
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498082"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="96bcb-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="96bcb-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="96bcb-103">取得處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="96bcb-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96bcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="96bcb-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96bcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="96bcb-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="96bcb-106">[out]指標`HPROCESS`也就是處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="96bcb-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96bcb-107">備註</span><span class="sxs-lookup"><span data-stu-id="96bcb-107">Remarks</span></span>  
 <span data-ttu-id="96bcb-108">擷取的控制代碼是由偵錯介面所擁有。</span><span class="sxs-lookup"><span data-stu-id="96bcb-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="96bcb-109">偵錯工具應該重複使用它之前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="96bcb-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96bcb-110">需求</span><span class="sxs-lookup"><span data-stu-id="96bcb-110">Requirements</span></span>  
 <span data-ttu-id="96bcb-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96bcb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96bcb-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96bcb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96bcb-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96bcb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96bcb-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96bcb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
