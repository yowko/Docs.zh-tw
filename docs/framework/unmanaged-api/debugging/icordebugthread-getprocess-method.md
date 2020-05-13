---
title: ICorDebugThread::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 76dfc10b9d9069f6d53cd292f241ae3080c6443a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379800"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="c4b46-102">ICorDebugThread::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="c4b46-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="c4b46-103">取得此 ICorDebugThread 構成元件之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="c4b46-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b46-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4b46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4b46-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4b46-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="c4b46-106">脫銷代表進程之 ICorDebugProcess 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c4b46-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b46-107">需求</span><span class="sxs-lookup"><span data-stu-id="c4b46-107">Requirements</span></span>  
 <span data-ttu-id="c4b46-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4b46-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b46-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b46-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b46-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b46-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b46-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b46-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
