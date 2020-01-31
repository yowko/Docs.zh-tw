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
ms.openlocfilehash: c2a176764332eed6affda704c8bfaf546ef70880
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788993"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="d124e-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="d124e-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="d124e-103">取得正在進行調試之進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d124e-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d124e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d124e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d124e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d124e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="d124e-106">ICorDebugProcessEnum 物件位址的指標，這是正在進行調試進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d124e-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d124e-107">需求</span><span class="sxs-lookup"><span data-stu-id="d124e-107">Requirements</span></span>  
 <span data-ttu-id="d124e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d124e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d124e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d124e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d124e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d124e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d124e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d124e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d124e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="d124e-112">See also</span></span>

- [<span data-ttu-id="d124e-113">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="d124e-113">ICorDebug Interface</span></span>](icordebug-interface.md)
