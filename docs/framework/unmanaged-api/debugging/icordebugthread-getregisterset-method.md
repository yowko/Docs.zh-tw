---
title: ICorDebugThread::GetRegisterSet 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: 9793424e79ed878b04a5c51daad08b5d12d439e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791459"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="56bbd-102">ICorDebugThread::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="56bbd-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="56bbd-103">取得與這個 ICorDebugThread 物件的使用中部分相關聯之暫存器集合的介面指標。</span><span class="sxs-lookup"><span data-stu-id="56bbd-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56bbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="56bbd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56bbd-105">參數</span><span class="sxs-lookup"><span data-stu-id="56bbd-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="56bbd-106">脫銷[ICorDebugRegisterSet](icordebugregisterset-interface.md)介面物件位址的指標，表示這個執行緒之使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="56bbd-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56bbd-107">需求</span><span class="sxs-lookup"><span data-stu-id="56bbd-107">Requirements</span></span>  
 <span data-ttu-id="56bbd-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56bbd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56bbd-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56bbd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56bbd-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56bbd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56bbd-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56bbd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
