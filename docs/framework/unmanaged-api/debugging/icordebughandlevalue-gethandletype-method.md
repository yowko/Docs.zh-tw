---
title: ICorDebugHandleValue::GetHandleType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: bc7d99d0ddb443cba227b7bad0cd53edb94c9101
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138546"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="ff0fb-102">ICorDebugHandleValue::GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="ff0fb-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="ff0fb-103">取得值，指出這個 ICorDebugHandleValue 物件所參考的控制碼種類。</span><span class="sxs-lookup"><span data-stu-id="ff0fb-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff0fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff0fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff0fb-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="ff0fb-106">脫銷CorDebugHandleType 列舉值的指標，指出這個控制碼的類型。</span><span class="sxs-lookup"><span data-stu-id="ff0fb-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0fb-107">需求</span><span class="sxs-lookup"><span data-stu-id="ff0fb-107">Requirements</span></span>  
 <span data-ttu-id="ff0fb-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff0fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff0fb-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff0fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff0fb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff0fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff0fb-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff0fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
