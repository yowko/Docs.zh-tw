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
ms.openlocfilehash: 72ef9a0fe4cd08ce67594600375953c249243d4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734149"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="2334d-102">ICorDebugHandleValue::GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="2334d-102">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="2334d-103">取得值，這個值表示這個 ICorDebugHandleValue 物件所參考的控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="2334d-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2334d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2334d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2334d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2334d-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="2334d-106">擴展CorDebugHandleType 列舉值的指標，指出這個控制碼的型別。</span><span class="sxs-lookup"><span data-stu-id="2334d-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2334d-107">需求</span><span class="sxs-lookup"><span data-stu-id="2334d-107">Requirements</span></span>  

 <span data-ttu-id="2334d-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2334d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2334d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2334d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2334d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2334d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2334d-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2334d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
