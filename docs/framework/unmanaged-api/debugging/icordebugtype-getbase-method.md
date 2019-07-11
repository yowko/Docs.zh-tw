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
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772043"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="91b46-102">ICorDebugType::GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="91b46-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="91b46-103">取得的介面指標來代表基底型別，如果有的話，表示這個型別的 ICorDebugType `ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="91b46-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b46-104">語法</span><span class="sxs-lookup"><span data-stu-id="91b46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b46-105">參數</span><span class="sxs-lookup"><span data-stu-id="91b46-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="91b46-106">[out]位址指標`ICorDebugType`表示基底型別的物件。</span><span class="sxs-lookup"><span data-stu-id="91b46-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91b46-107">備註</span><span class="sxs-lookup"><span data-stu-id="91b46-107">Remarks</span></span>  
 <span data-ttu-id="91b46-108">查閱基底型別是有用來實作常見的偵錯工具功能，例如列印出的物件或其父類別的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="91b46-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b46-109">需求</span><span class="sxs-lookup"><span data-stu-id="91b46-109">Requirements</span></span>  
 <span data-ttu-id="91b46-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91b46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91b46-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91b46-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91b46-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91b46-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91b46-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91b46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
