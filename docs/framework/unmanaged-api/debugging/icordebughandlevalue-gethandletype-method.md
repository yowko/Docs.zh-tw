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
ms.openlocfilehash: 6eb76ddd6ee8b2a00aac3af9ebf815338d29f194
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212161"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="c55ac-102">ICorDebugHandleValue::GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="c55ac-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="c55ac-103">取得值，指出這個 ICorDebugHandleValue 物件所參考的控制碼種類。</span><span class="sxs-lookup"><span data-stu-id="c55ac-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="c55ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c55ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="c55ac-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="c55ac-106">脫銷CorDebugHandleType 列舉值的指標，指出這個控制碼的類型。</span><span class="sxs-lookup"><span data-stu-id="c55ac-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55ac-107">需求</span><span class="sxs-lookup"><span data-stu-id="c55ac-107">Requirements</span></span>  
 <span data-ttu-id="c55ac-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c55ac-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55ac-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c55ac-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c55ac-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c55ac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c55ac-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c55ac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
