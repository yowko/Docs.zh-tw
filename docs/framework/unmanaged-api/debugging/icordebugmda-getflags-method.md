---
title: ICorDebugMDA::GetFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 4e5939e9e74899a33f28927c4fda09d0a8fb30a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209730"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="5bc03-102">ICorDebugMDA::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="5bc03-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="5bc03-103">取得與[ICorDebugMDA](icordebugmda-interface.md)代表的 managed 偵錯工具（MDA）相關聯的旗標。</span><span class="sxs-lookup"><span data-stu-id="5bc03-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc03-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bc03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc03-105">參數</span><span class="sxs-lookup"><span data-stu-id="5bc03-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="5bc03-106">在[CorDebugMDAFlags](cordebugmdaflags-enumeration.md)列舉值的位元組合，指定此 MDA 的旗標設定。</span><span class="sxs-lookup"><span data-stu-id="5bc03-106">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc03-107">需求</span><span class="sxs-lookup"><span data-stu-id="5bc03-107">Requirements</span></span>  
 <span data-ttu-id="5bc03-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bc03-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc03-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bc03-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bc03-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc03-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc03-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc03-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc03-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="5bc03-112">See also</span></span>

- [<span data-ttu-id="5bc03-113">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="5bc03-113">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="5bc03-114">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="5bc03-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
