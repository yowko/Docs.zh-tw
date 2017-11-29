---
title: "ICorDebugStepper2::SetJMC 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper2.SetJMC
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b34e0d612957da1ec1ca3535bfa1a0d7a5bae5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="20f4f-102">ICorDebugStepper2::SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="20f4f-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="20f4f-103">設定值，指定這個 ICorDebugStepper 是否只能透過應用程式的開發人員所撰寫的程式碼的步驟。</span><span class="sxs-lookup"><span data-stu-id="20f4f-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="20f4f-104">此程序也稱為 my code (JMC) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="20f4f-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f4f-105">語法</span><span class="sxs-lookup"><span data-stu-id="20f4f-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20f4f-106">參數</span><span class="sxs-lookup"><span data-stu-id="20f4f-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="20f4f-107">[in]設定為`true`來逐步執行程式碼，是應用程式的開發人員撰寫; 否則設定為只`false`。</span><span class="sxs-lookup"><span data-stu-id="20f4f-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f4f-108">需求</span><span class="sxs-lookup"><span data-stu-id="20f4f-108">Requirements</span></span>  
 <span data-ttu-id="20f4f-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20f4f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f4f-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20f4f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20f4f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20f4f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20f4f-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
