---
title: ICorDebug::EnumerateProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bc82c506cf7e223e672a62ca74b215cac870e50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989534"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="3b00a-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="3b00a-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="3b00a-103">取得正在偵錯的處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3b00a-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b00a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b00a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b00a-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b00a-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="3b00a-106">ICorDebugProcessEnum 物件的列舉程式進行偵錯的處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="3b00a-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b00a-107">需求</span><span class="sxs-lookup"><span data-stu-id="3b00a-107">Requirements</span></span>  
 <span data-ttu-id="3b00a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b00a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b00a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b00a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b00a-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b00a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b00a-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b00a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b00a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b00a-112">See also</span></span>

- [<span data-ttu-id="3b00a-113">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="3b00a-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
