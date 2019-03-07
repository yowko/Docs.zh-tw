---
title: ICorDebugStepper2::SetJMC 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 129bf04a097b2019b080f813bf049d41b501f8fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474211"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="4f4d3-102">ICorDebugStepper2::SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="4f4d3-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="4f4d3-103">設定值，這個值指出是否此 ICorDebugStepper 步驟只能透過應用程式的開發人員所撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f4d3-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="4f4d3-104">此程序也稱為 my code (JMC) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="4f4d3-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f4d3-105">語法</span><span class="sxs-lookup"><span data-stu-id="4f4d3-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f4d3-106">參數</span><span class="sxs-lookup"><span data-stu-id="4f4d3-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="4f4d3-107">[in]設定為`true`來逐步執行程式碼，是由應用程式的開發人員所撰寫; 否則設定為只`false`。</span><span class="sxs-lookup"><span data-stu-id="4f4d3-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f4d3-108">需求</span><span class="sxs-lookup"><span data-stu-id="4f4d3-108">Requirements</span></span>  
 <span data-ttu-id="4f4d3-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4d3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f4d3-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f4d3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f4d3-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f4d3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f4d3-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f4d3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
