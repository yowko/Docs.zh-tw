---
title: ICorDebugType::GetBase 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478722"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="1ea15-102">ICorDebugType::GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="1ea15-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="1ea15-103">取得的介面指標來代表基底型別，如果有的話，表示這個型別的 ICorDebugType `ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="1ea15-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea15-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ea15-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ea15-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ea15-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="1ea15-106">[out]位址指標`ICorDebugType`表示基底型別的物件。</span><span class="sxs-lookup"><span data-stu-id="1ea15-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ea15-107">備註</span><span class="sxs-lookup"><span data-stu-id="1ea15-107">Remarks</span></span>  
 <span data-ttu-id="1ea15-108">查閱基底型別是有用來實作常見的偵錯工具功能，例如列印出的物件或其父類別的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="1ea15-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea15-109">需求</span><span class="sxs-lookup"><span data-stu-id="1ea15-109">Requirements</span></span>  
 <span data-ttu-id="1ea15-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea15-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ea15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ea15-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ea15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ea15-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
