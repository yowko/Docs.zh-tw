---
title: ICorDebugFrame::GetChain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: cab25738c9f4727fe3970cc1db15c38e68b08de6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212915"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="8aaa4-102">ICorDebugFrame::GetChain 方法</span><span class="sxs-lookup"><span data-stu-id="8aaa4-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="8aaa4-103">取得此框架所屬之鏈的指標。</span><span class="sxs-lookup"><span data-stu-id="8aaa4-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aaa4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8aaa4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aaa4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8aaa4-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="8aaa4-106">脫銷ICorDebugChain 物件位址的指標，表示包含此框架的鏈。</span><span class="sxs-lookup"><span data-stu-id="8aaa4-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aaa4-107">需求</span><span class="sxs-lookup"><span data-stu-id="8aaa4-107">Requirements</span></span>  
 <span data-ttu-id="8aaa4-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8aaa4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aaa4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aaa4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aaa4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aaa4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aaa4-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aaa4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
