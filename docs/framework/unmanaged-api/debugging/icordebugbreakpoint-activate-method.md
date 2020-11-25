---
title: ICorDebugBreakpoint::Activate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 70a07f0ce7f1fa4c904fde594dcf82c5149616fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721526"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="891ff-102">ICorDebugBreakpoint::Activate 方法</span><span class="sxs-lookup"><span data-stu-id="891ff-102">ICorDebugBreakpoint::Activate Method</span></span>

<span data-ttu-id="891ff-103">設定這個的作用中狀態 `ICorDebugBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="891ff-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="891ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="891ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="891ff-105">Parameters</span></span>  

 `bActive`  
 <span data-ttu-id="891ff-106">在將此值設定為，以將狀態指定為作用中 `true` ; 否則，請將此值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="891ff-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="891ff-107">需求</span><span class="sxs-lookup"><span data-stu-id="891ff-107">Requirements</span></span>  

 <span data-ttu-id="891ff-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="891ff-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="891ff-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="891ff-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="891ff-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="891ff-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="891ff-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="891ff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
