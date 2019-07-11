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
ms.openlocfilehash: 9ebdf0dd2457cd10e31ff71c32b1c09d0e014431
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765994"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="df25f-102">ICorDebugProcess::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="df25f-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="df25f-103">取得處理序的作業系統 (OS) 識別碼。</span><span class="sxs-lookup"><span data-stu-id="df25f-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df25f-104">語法</span><span class="sxs-lookup"><span data-stu-id="df25f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df25f-105">參數</span><span class="sxs-lookup"><span data-stu-id="df25f-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="df25f-106">[out]處理序的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="df25f-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df25f-107">需求</span><span class="sxs-lookup"><span data-stu-id="df25f-107">Requirements</span></span>  
 <span data-ttu-id="df25f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df25f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df25f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df25f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df25f-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df25f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df25f-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df25f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
