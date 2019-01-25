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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b4cf6c50d624f82a75f19b8e3f42c73910c4e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709295"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="98598-102">ICorDebug::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="98598-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="98598-103">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="98598-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98598-104">語法</span><span class="sxs-lookup"><span data-stu-id="98598-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="98598-105">備註</span><span class="sxs-lookup"><span data-stu-id="98598-105">Remarks</span></span>  
 <span data-ttu-id="98598-106">偵錯工具必須呼叫`Initialize`在建立時的時間來初始化偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="98598-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="98598-107">必須在任何其他方法之前呼叫這個方法`ICorDebug`呼叫。</span><span class="sxs-lookup"><span data-stu-id="98598-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98598-108">需求</span><span class="sxs-lookup"><span data-stu-id="98598-108">Requirements</span></span>  
 <span data-ttu-id="98598-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98598-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98598-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98598-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98598-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98598-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98598-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98598-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98598-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98598-113">See also</span></span>
- [<span data-ttu-id="98598-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="98598-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
