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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8769293364c111754f4bfe9360a0dca93c0ba13c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770601"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="4d6e3-102">ICorDebugThread::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="4d6e3-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="4d6e3-103">取得與這個 ICorDebugThread 物件的使用中部分相關聯的暫存器集的介面指標。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d6e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d6e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d6e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d6e3-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="4d6e3-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)介面的物件，代表註冊為此執行緒的使用中部分。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d6e3-107">需求</span><span class="sxs-lookup"><span data-stu-id="4d6e3-107">Requirements</span></span>  
 <span data-ttu-id="4d6e3-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d6e3-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d6e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d6e3-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d6e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d6e3-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d6e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
