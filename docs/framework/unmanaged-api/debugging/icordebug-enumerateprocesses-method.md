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
ms.openlocfilehash: 14a2fa36393135a1e5ccecb69879113a62a9d065
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895393"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="f7067-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="f7067-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="f7067-103">取得正在進行調試之進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f7067-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7067-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7067-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7067-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7067-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="f7067-106">ICorDebugProcessEnum 物件位址的指標，這是正在進行調試進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f7067-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7067-107">需求</span><span class="sxs-lookup"><span data-stu-id="f7067-107">Requirements</span></span>  
 <span data-ttu-id="f7067-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7067-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7067-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7067-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7067-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7067-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7067-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7067-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7067-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7067-112">See also</span></span>

- [<span data-ttu-id="f7067-113">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="f7067-113">ICorDebug Interface</span></span>](icordebug-interface.md)
