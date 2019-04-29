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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c20eec52b0e4616af1b864bb58b6cbff44a720eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645392"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="e3207-102">ICorDebugBoxValue::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="e3207-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="e3207-103">取得 boxed 的值。</span><span class="sxs-lookup"><span data-stu-id="e3207-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3207-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3207-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3207-105">參數</span><span class="sxs-lookup"><span data-stu-id="e3207-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e3207-106">[out]ICorDebugObjectValue 物件，表示 boxed 的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e3207-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3207-107">需求</span><span class="sxs-lookup"><span data-stu-id="e3207-107">Requirements</span></span>  
 <span data-ttu-id="e3207-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3207-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3207-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3207-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3207-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3207-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3207-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3207-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
