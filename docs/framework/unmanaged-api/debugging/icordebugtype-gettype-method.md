---
title: "ICorDebugType::GetType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20e2a1415d5dda9c4097d984af46942ebcf2365a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="70ec6-102">ICorDebugType::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="70ec6-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="70ec6-103">取得 CorElementType 值描述 common language runtime (CLR) 的原生類型<xref:System.Type>此 ICorDebugType 所表示。</span><span class="sxs-lookup"><span data-stu-id="70ec6-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ec6-104">語法</span><span class="sxs-lookup"><span data-stu-id="70ec6-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70ec6-105">參數</span><span class="sxs-lookup"><span data-stu-id="70ec6-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="70ec6-106">[out]值的指標`CorElementType`列舉，指出 CLR<xref:System.Type>這個`ICorDebugType`代表。</span><span class="sxs-lookup"><span data-stu-id="70ec6-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70ec6-107">備註</span><span class="sxs-lookup"><span data-stu-id="70ec6-107">Remarks</span></span>  
 <span data-ttu-id="70ec6-108">如果值`ty`ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE， [icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)方法可能會呼叫以取得泛型類型的未具現化的類型; 否則請勿呼叫`ICorDebugType::GetClass`。</span><span class="sxs-lookup"><span data-stu-id="70ec6-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ec6-109">需求</span><span class="sxs-lookup"><span data-stu-id="70ec6-109">Requirements</span></span>  
 <span data-ttu-id="70ec6-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70ec6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ec6-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70ec6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70ec6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70ec6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70ec6-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ec6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
