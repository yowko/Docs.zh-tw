---
title: ICorDebugBoxValue::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: 475cc6c688262f318aa7f844b975ad69fa80bbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122827"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="f3b6b-102">ICorDebugBoxValue::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="f3b6b-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="f3b6b-103">取得已裝箱的值。</span><span class="sxs-lookup"><span data-stu-id="f3b6b-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3b6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3b6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3b6b-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="f3b6b-106">脫銷代表已裝箱值之 ICorDebugObjectValue 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="f3b6b-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b6b-107">需求</span><span class="sxs-lookup"><span data-stu-id="f3b6b-107">Requirements</span></span>  
 <span data-ttu-id="f3b6b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b6b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b6b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3b6b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3b6b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3b6b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3b6b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b6b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
