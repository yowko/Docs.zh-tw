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
ms.openlocfilehash: 6bf73a4be40f1fbd8e9d37477907001604e8e4a6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128825"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="6a6b5-102">ICorDebugProcess::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="6a6b5-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="6a6b5-103">取得這個進程的執行緒，其具有指定的作業系統（OS）執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a6b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a6b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a6b5-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="6a6b5-106">在要抓取之執行緒的 OS 執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="6a6b5-107">脫銷代表執行緒之 ICorDebugThread 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6b5-108">需求</span><span class="sxs-lookup"><span data-stu-id="6a6b5-108">Requirements</span></span>  
 <span data-ttu-id="6a6b5-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a6b5-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a6b5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a6b5-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a6b5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a6b5-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a6b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
