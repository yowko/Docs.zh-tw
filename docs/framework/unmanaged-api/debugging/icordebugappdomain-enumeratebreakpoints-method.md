---
title: "ICorDebugAppDomain::EnumerateBreakpoints 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateBreakpoints
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a29bb5b8a21a9d8082564ec377edc20cd62378a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="bca3e-102">ICorDebugAppDomain::EnumerateBreakpoints 方法</span><span class="sxs-lookup"><span data-stu-id="bca3e-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="bca3e-103">應用程式定義域中取得所有作用中的中斷點的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bca3e-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="bca3e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="bca3e-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="bca3e-106">[out]ICorDebugBreakpointEnum 物件，為所有使用中的中斷點，應用程式定義域中的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bca3e-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca3e-107">備註</span><span class="sxs-lookup"><span data-stu-id="bca3e-107">Remarks</span></span>  
 <span data-ttu-id="bca3e-108">此列舉值會包含所有類型的中斷點，包括函式中斷點和資料中斷點。</span><span class="sxs-lookup"><span data-stu-id="bca3e-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca3e-109">需求</span><span class="sxs-lookup"><span data-stu-id="bca3e-109">Requirements</span></span>  
 <span data-ttu-id="bca3e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bca3e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca3e-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bca3e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bca3e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bca3e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bca3e-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
