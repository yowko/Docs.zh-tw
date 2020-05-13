---
title: ICorDebugReferenceValue::Dereference 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: 7c64823e1a5c519eb74b508af093afeb1132e608
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210081"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="d070f-102">ICorDebugReferenceValue::Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="d070f-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="d070f-103">取得所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="d070f-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d070f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d070f-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d070f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d070f-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="d070f-106">脫銷ICorDebugValue 位址的指標，代表這個 ICorDebugReferenceValue 物件指向的物件。</span><span class="sxs-lookup"><span data-stu-id="d070f-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d070f-107">備註</span><span class="sxs-lookup"><span data-stu-id="d070f-107">Remarks</span></span>  
 <span data-ttu-id="d070f-108">`ICorDebugValue`只有在參考尚未停用時，物件才有效。</span><span class="sxs-lookup"><span data-stu-id="d070f-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d070f-109">需求</span><span class="sxs-lookup"><span data-stu-id="d070f-109">Requirements</span></span>  
 <span data-ttu-id="d070f-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d070f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d070f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d070f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d070f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d070f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d070f-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d070f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
