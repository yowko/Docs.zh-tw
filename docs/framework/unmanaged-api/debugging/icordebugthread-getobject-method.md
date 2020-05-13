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
ms.openlocfilehash: 624469ca1ae4c96b4143f8768b4c5ff9c2601a2f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378876"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="94e10-102">ICorDebugThread::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="94e10-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="94e10-103">取得 common language runtime （CLR）執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="94e10-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e10-104">語法</span><span class="sxs-lookup"><span data-stu-id="94e10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94e10-105">參數</span><span class="sxs-lookup"><span data-stu-id="94e10-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="94e10-106">脫銷表示 CLR 執行緒之 ICorDebugValue 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="94e10-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94e10-107">需求</span><span class="sxs-lookup"><span data-stu-id="94e10-107">Requirements</span></span>  
 <span data-ttu-id="94e10-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94e10-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94e10-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94e10-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94e10-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94e10-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94e10-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94e10-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e10-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94e10-112">See also</span></span>

- <xref:System.Threading.Thread>
