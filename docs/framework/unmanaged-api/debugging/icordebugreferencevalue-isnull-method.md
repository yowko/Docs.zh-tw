---
title: "ICorDebugReferenceValue::IsNull 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.IsNull
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8a7892900149380c979f0bee1a4229407af8c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="4e737-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="4e737-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="4e737-103">取得值，指出此 ICorDebugReferenceValue 是否為 null 值，在此情況下`ICorDebugReferenceValue`未指向物件。</span><span class="sxs-lookup"><span data-stu-id="4e737-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e737-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e737-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e737-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e737-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="4e737-106">[out]為的布林值的指標`true`如果這個`ICorDebugReferenceValue`物件為 null; 否則`pbNull`是`false`。</span><span class="sxs-lookup"><span data-stu-id="4e737-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e737-107">需求</span><span class="sxs-lookup"><span data-stu-id="4e737-107">Requirements</span></span>  
 <span data-ttu-id="4e737-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e737-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e737-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e737-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e737-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e737-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e737-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e737-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
