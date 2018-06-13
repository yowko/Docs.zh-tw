---
title: ICorDebugArrayValue::GetDimensions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9c341ba3d0164e65cd752baa20f674fe3afc714
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405430"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="b8a4d-102">ICorDebugArrayValue::GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="b8a4d-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="b8a4d-103">取得這個陣列的每個維度中的項目數目。</span><span class="sxs-lookup"><span data-stu-id="b8a4d-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8a4d-104">Syntax</span></span>  
  
```  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8a4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8a4d-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="b8a4d-106">[in]這個 ICorDebugArrayValue 物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="b8a4d-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="b8a4d-107">此值也是大小`dims`因為其大小的維度數目等於陣列`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="b8a4d-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="b8a4d-108">[out]整數的陣列，其中每個在此維度中指定的項目數`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="b8a4d-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a4d-109">需求</span><span class="sxs-lookup"><span data-stu-id="b8a4d-109">Requirements</span></span>  
 <span data-ttu-id="b8a4d-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a4d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a4d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8a4d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8a4d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8a4d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8a4d-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a4d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
