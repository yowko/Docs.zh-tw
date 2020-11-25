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
ms.openlocfilehash: 1bbcbcfbb78d421f247a13f58070b68f701e4ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697203"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="47c86-102">ICorDebugStepper2::SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="47c86-102">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="47c86-103">設定值，這個值會指定此 ICorDebugStepper 是否只透過應用程式開發人員所撰寫的程式碼進行步驟。</span><span class="sxs-lookup"><span data-stu-id="47c86-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="47c86-104">此程式也稱為「我的程式碼 (JMC) 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="47c86-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c86-105">語法</span><span class="sxs-lookup"><span data-stu-id="47c86-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47c86-106">參數</span><span class="sxs-lookup"><span data-stu-id="47c86-106">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="47c86-107">在若設定為 `true` ，則只會透過應用程式開發人員所撰寫的程式碼進行步驟; 否則，請將設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="47c86-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47c86-108">需求</span><span class="sxs-lookup"><span data-stu-id="47c86-108">Requirements</span></span>  

 <span data-ttu-id="47c86-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47c86-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47c86-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47c86-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47c86-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47c86-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47c86-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47c86-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
