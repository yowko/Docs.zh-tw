---
title: ICorDebugProcess::GetThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5cbdd19fa14a41d8bd2eadec80dbafcea7b720d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766439"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="bfb4d-102">ICorDebugProcess::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="bfb4d-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="bfb4d-103">取得這個處理程序的執行緒，其具有指定的作業系統 (OS) 執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="bfb4d-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfb4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfb4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfb4d-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="bfb4d-106">[in]OS 執行緒要擷取之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bfb4d-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="bfb4d-107">[out]ICorDebugThread 物件，表示執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bfb4d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb4d-108">需求</span><span class="sxs-lookup"><span data-stu-id="bfb4d-108">Requirements</span></span>  
 <span data-ttu-id="bfb4d-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb4d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb4d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfb4d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfb4d-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfb4d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfb4d-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb4d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
