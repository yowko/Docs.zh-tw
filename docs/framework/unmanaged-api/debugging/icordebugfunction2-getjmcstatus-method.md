---
title: ICorDebugFunction2::GetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988659"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="33281-102">ICorDebugFunction2::GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="33281-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="33281-103">取得值，指出是否要將此 ICorDebugFunction2 物件所代表的函式標記為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="33281-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33281-104">語法</span><span class="sxs-lookup"><span data-stu-id="33281-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33281-105">參數</span><span class="sxs-lookup"><span data-stu-id="33281-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="33281-106">[out]布林值的指標`true`，則此函式標示為使用者程式碼; 否則值就是`false`。</span><span class="sxs-lookup"><span data-stu-id="33281-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33281-107">備註</span><span class="sxs-lookup"><span data-stu-id="33281-107">Remarks</span></span>  
 <span data-ttu-id="33281-108">如果函式以表示這`ICorDebugFunction2`無法偵錯，`pbIsJustMyCode`一定會`false`。</span><span class="sxs-lookup"><span data-stu-id="33281-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33281-109">需求</span><span class="sxs-lookup"><span data-stu-id="33281-109">Requirements</span></span>  
 <span data-ttu-id="33281-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33281-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33281-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33281-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33281-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33281-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33281-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33281-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
