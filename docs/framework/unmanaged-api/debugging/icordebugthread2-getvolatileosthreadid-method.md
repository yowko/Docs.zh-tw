---
title: ICorDebugThread2::GetVolatileOSThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: e8d59d617efa7656a3034d5c5e009a46b6121cdb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377651"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="92903-102">ICorDebugThread2::GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="92903-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="92903-103">取得此 ICorDebugThread2 的作業系統執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="92903-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92903-104">語法</span><span class="sxs-lookup"><span data-stu-id="92903-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92903-105">參數</span><span class="sxs-lookup"><span data-stu-id="92903-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="92903-106">脫銷此執行緒的作業系統執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="92903-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92903-107">需求</span><span class="sxs-lookup"><span data-stu-id="92903-107">Requirements</span></span>  
 <span data-ttu-id="92903-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92903-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92903-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92903-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92903-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92903-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92903-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92903-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
