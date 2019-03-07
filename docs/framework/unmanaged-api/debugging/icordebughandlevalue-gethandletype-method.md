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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecc0b46618cd00ba4442e30c23a7b7e950382fee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475589"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="1c21f-102">ICorDebugHandleValue::GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="1c21f-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="1c21f-103">取得值，指出此 ICorDebugHandleValue 物件所參考的控制代碼的類型。</span><span class="sxs-lookup"><span data-stu-id="1c21f-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c21f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c21f-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c21f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c21f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="1c21f-106">[out]CorDebugHandleType 列舉，指出這個控制代碼類型的值的指標。</span><span class="sxs-lookup"><span data-stu-id="1c21f-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c21f-107">需求</span><span class="sxs-lookup"><span data-stu-id="1c21f-107">Requirements</span></span>  
 <span data-ttu-id="1c21f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c21f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c21f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c21f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c21f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c21f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c21f-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c21f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
