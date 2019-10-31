---
title: ICorDebugThread::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: 5cb95fb7cf70dbf7616e9bc59ebf44de090de883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133438"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="e8579-102">ICorDebugThread::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="e8579-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="e8579-103">取得 common language runtime （CLR）執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e8579-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8579-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8579-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8579-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8579-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e8579-106">脫銷表示 CLR 執行緒之 ICorDebugValue 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e8579-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8579-107">需求</span><span class="sxs-lookup"><span data-stu-id="e8579-107">Requirements</span></span>  
 <span data-ttu-id="e8579-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8579-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8579-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8579-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8579-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8579-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8579-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8579-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8579-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8579-112">See also</span></span>

- <xref:System.Threading.Thread>
