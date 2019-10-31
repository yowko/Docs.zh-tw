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
ms.openlocfilehash: 6c076dd2912a22e4f9492492a2d7a9fb73db88e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139031"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="87269-102">ICorDebugStepper2::SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="87269-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="87269-103">設定值，指定此 ICorDebugStepper 步驟是否只透過應用程式開發人員所撰寫的程式碼進行。</span><span class="sxs-lookup"><span data-stu-id="87269-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="87269-104">這個程式也就是所謂的「我的程式碼」（JMC）偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="87269-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87269-105">語法</span><span class="sxs-lookup"><span data-stu-id="87269-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87269-106">參數</span><span class="sxs-lookup"><span data-stu-id="87269-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="87269-107">在設定為 `true`，只透過應用程式開發人員所撰寫的程式碼執行。否則，請將設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="87269-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87269-108">需求</span><span class="sxs-lookup"><span data-stu-id="87269-108">Requirements</span></span>  
 <span data-ttu-id="87269-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87269-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87269-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87269-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87269-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87269-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87269-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87269-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
