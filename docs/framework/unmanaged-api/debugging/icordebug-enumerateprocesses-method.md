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
ms.openlocfilehash: 53d40c198b53370733009c76fd3d49f14df93e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402092"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="3241e-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="3241e-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="3241e-103">取得正在進行偵錯的處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3241e-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3241e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3241e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3241e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3241e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="3241e-106">ICorDebugProcessEnum 物件的列舉程式進行偵錯的處理程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="3241e-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3241e-107">需求</span><span class="sxs-lookup"><span data-stu-id="3241e-107">Requirements</span></span>  
 <span data-ttu-id="3241e-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3241e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3241e-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3241e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3241e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3241e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3241e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3241e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3241e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3241e-112">See Also</span></span>  
 [<span data-ttu-id="3241e-113">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="3241e-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
