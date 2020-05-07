---
title: ICorDebug::Initialize 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: aeecf19cb85ce5d7781c3dfedca079e97cab76ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895349"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="4b3c3-102">ICorDebug::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="4b3c3-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="4b3c3-103">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="4b3c3-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b3c3-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b3c3-105">備註</span><span class="sxs-lookup"><span data-stu-id="4b3c3-105">Remarks</span></span>  
 <span data-ttu-id="4b3c3-106">偵錯工具在建立`Initialize`時必須呼叫來初始化偵錯工具服務。</span><span class="sxs-lookup"><span data-stu-id="4b3c3-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="4b3c3-107">在呼叫上的`ICorDebug`任何其他方法之前，必須先呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="4b3c3-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3c3-108">需求</span><span class="sxs-lookup"><span data-stu-id="4b3c3-108">Requirements</span></span>  
 <span data-ttu-id="4b3c3-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b3c3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3c3-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b3c3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b3c3-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b3c3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b3c3-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3c3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3c3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b3c3-113">See also</span></span>

- [<span data-ttu-id="4b3c3-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="4b3c3-114">ICorDebug Interface</span></span>](icordebug-interface.md)
