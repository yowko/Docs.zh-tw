---
title: "ICorDebugProcess::GetThread 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 996003f254c5150dfd39ca62d7cadf07282596c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="fffc8-102">ICorDebugProcess::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="fffc8-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="fffc8-103">取得這個處理序的執行緒，其具有指定的作業系統 (OS) 執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="fffc8-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="fffc8-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fffc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="fffc8-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="fffc8-106">[in]OS 執行緒要擷取之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fffc8-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="fffc8-107">[out]ICorDebugThread 物件，表示執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fffc8-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fffc8-108">需求</span><span class="sxs-lookup"><span data-stu-id="fffc8-108">Requirements</span></span>  
 <span data-ttu-id="fffc8-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fffc8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fffc8-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fffc8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fffc8-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fffc8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fffc8-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffc8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
