---
title: ICorDebugProcess::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9239ccfe8ce08e5b50b762a6fede11ab8a439b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495711"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="8275e-102">ICorDebugProcess::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="8275e-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="8275e-103">取得處理序的作業系統 (OS) 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8275e-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8275e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8275e-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8275e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8275e-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="8275e-106">[out]處理序的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8275e-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8275e-107">需求</span><span class="sxs-lookup"><span data-stu-id="8275e-107">Requirements</span></span>  
 <span data-ttu-id="8275e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8275e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8275e-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8275e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8275e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8275e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8275e-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8275e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
