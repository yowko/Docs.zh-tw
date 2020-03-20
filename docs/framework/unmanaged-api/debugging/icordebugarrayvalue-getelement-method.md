---
title: ICorDebugArrayValue::GetElement 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179015"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="7765f-102">ICorDebugArrayValue::GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="7765f-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="7765f-103">獲取給定陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="7765f-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7765f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7765f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7765f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7765f-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="7765f-106">[在]此`ICorDebugArrayValue`物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="7765f-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="7765f-107">此值也是陣列的大小，`indices`因為它的大小等於`ICorDebugArrayValue`物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="7765f-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="7765f-108">[在]索引值陣列，每個陣列指定`ICorDebugArrayValue`物件維度中的位置。</span><span class="sxs-lookup"><span data-stu-id="7765f-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="7765f-109">此值不能為空。</span><span class="sxs-lookup"><span data-stu-id="7765f-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7765f-110">[出]指向 ICorDebugValue 物件位址的指標，表示指定元素的值。</span><span class="sxs-lookup"><span data-stu-id="7765f-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7765f-111">需求</span><span class="sxs-lookup"><span data-stu-id="7765f-111">Requirements</span></span>  
 <span data-ttu-id="7765f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7765f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7765f-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7765f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7765f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7765f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7765f-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7765f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
