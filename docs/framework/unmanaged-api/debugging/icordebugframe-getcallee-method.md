---
title: ICorDebugFrame::GetCallee 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 51ac10f936db129282720f2bcae8729f56735b59
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205373"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="e75e9-102">ICorDebugFrame::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="e75e9-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="e75e9-103">取得此框架所呼叫之目前鏈中 ICorDebugFrame 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e75e9-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e75e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e75e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e75e9-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="e75e9-106">脫銷物件位址的指標 `ICorDebugFrame` ，代表所呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="e75e9-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="e75e9-107">如果呼叫框架是目前鏈中最內層的框架，則此值為 null。</span><span class="sxs-lookup"><span data-stu-id="e75e9-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e75e9-108">需求</span><span class="sxs-lookup"><span data-stu-id="e75e9-108">Requirements</span></span>  
 <span data-ttu-id="e75e9-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e75e9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e75e9-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e75e9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e75e9-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e75e9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e75e9-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e75e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
