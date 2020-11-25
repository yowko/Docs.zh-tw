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
ms.openlocfilehash: 5cdd89ebdbb5abb9b001c1489a54bfb867808c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723424"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="82665-102">ICorDebug::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="82665-102">ICorDebug::Initialize Method</span></span>

<span data-ttu-id="82665-103">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="82665-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82665-104">語法</span><span class="sxs-lookup"><span data-stu-id="82665-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="82665-105">備註</span><span class="sxs-lookup"><span data-stu-id="82665-105">Remarks</span></span>  

 <span data-ttu-id="82665-106">偵錯工具必須 `Initialize` 在建立時呼叫，以初始化偵錯工具服務。</span><span class="sxs-lookup"><span data-stu-id="82665-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="82665-107">在呼叫上的任何其他方法之前，必須先呼叫這個方法 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="82665-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82665-108">需求</span><span class="sxs-lookup"><span data-stu-id="82665-108">Requirements</span></span>  

 <span data-ttu-id="82665-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82665-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82665-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82665-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82665-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82665-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82665-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82665-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82665-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82665-113">See also</span></span>

- [<span data-ttu-id="82665-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="82665-114">ICorDebug Interface</span></span>](icordebug-interface.md)
