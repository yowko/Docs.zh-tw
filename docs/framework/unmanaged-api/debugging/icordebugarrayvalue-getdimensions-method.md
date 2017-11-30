---
title: "ICorDebugArrayValue::GetDimensions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetDimensions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 364035a0b6e26f5649ef9be5839d096be2fb02dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="604d5-102">ICorDebugArrayValue::GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="604d5-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="604d5-103">取得這個陣列的每個維度中的項目數目。</span><span class="sxs-lookup"><span data-stu-id="604d5-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="604d5-104">Syntax</span></span>  
  
```  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="604d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="604d5-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="604d5-106">[in]這個 ICorDebugArrayValue 物件的維度數目。</span><span class="sxs-lookup"><span data-stu-id="604d5-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="604d5-107">此值也是大小`dims`因為其大小的維度數目等於陣列`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="604d5-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="604d5-108">[out]整數的陣列，其中每個在此維度中指定的項目數`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="604d5-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604d5-109">需求</span><span class="sxs-lookup"><span data-stu-id="604d5-109">Requirements</span></span>  
 <span data-ttu-id="604d5-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="604d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="604d5-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="604d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="604d5-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="604d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="604d5-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="604d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
