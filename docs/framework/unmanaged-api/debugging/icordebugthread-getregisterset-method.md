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
ms.openlocfilehash: 7d3575909f54c8d676c9fd4246e6eac4a8a0ea1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727974"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="59569-102">ICorDebugThread::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="59569-102">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="59569-103">取得與這個 ICorDebugThread 物件之使用中部分相關聯之註冊集的介面指標。</span><span class="sxs-lookup"><span data-stu-id="59569-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59569-104">語法</span><span class="sxs-lookup"><span data-stu-id="59569-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59569-105">參數</span><span class="sxs-lookup"><span data-stu-id="59569-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="59569-106">擴展 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 介面物件位址的指標，該物件代表此執行緒之使用中部分的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="59569-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59569-107">需求</span><span class="sxs-lookup"><span data-stu-id="59569-107">Requirements</span></span>  

 <span data-ttu-id="59569-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59569-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59569-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59569-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59569-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59569-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59569-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59569-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
