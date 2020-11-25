---
title: ICorDebugStepper::Deactivate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 0d7d5e7e6c9bc1a68feda85c5214f3ae95df9b97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730561"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="ee508-102">ICorDebugStepper::Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="ee508-102">ICorDebugStepper::Deactivate Method</span></span>

<span data-ttu-id="ee508-103">導致此 ICorDebugStepper 取消它所收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="ee508-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee508-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee508-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ee508-105">備註</span><span class="sxs-lookup"><span data-stu-id="ee508-105">Remarks</span></span>  

 <span data-ttu-id="ee508-106">在取消最近收到的步驟命令之後，可能會發出新的逐步執行命令。</span><span class="sxs-lookup"><span data-stu-id="ee508-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee508-107">需求</span><span class="sxs-lookup"><span data-stu-id="ee508-107">Requirements</span></span>  

 <span data-ttu-id="ee508-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee508-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee508-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee508-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee508-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee508-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee508-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee508-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
