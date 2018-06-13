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
ms.openlocfilehash: b96c6ab8fb9065e1a08ad45a7f4482ef0b32788b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418879"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="46600-102">ICorDebugType::GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="46600-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="46600-103">取得的介面指標來代表基底類型中，如果有的話，表示這個型別的 ICorDebugType `ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="46600-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46600-104">語法</span><span class="sxs-lookup"><span data-stu-id="46600-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46600-105">參數</span><span class="sxs-lookup"><span data-stu-id="46600-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="46600-106">[out]位址指標`ICorDebugType`代表基底類型的物件。</span><span class="sxs-lookup"><span data-stu-id="46600-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46600-107">備註</span><span class="sxs-lookup"><span data-stu-id="46600-107">Remarks</span></span>  
 <span data-ttu-id="46600-108">查詢類型的基底類型適合實作常見的偵錯工具功能，例如列印出的物件或其父類別的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="46600-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46600-109">需求</span><span class="sxs-lookup"><span data-stu-id="46600-109">Requirements</span></span>  
 <span data-ttu-id="46600-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46600-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46600-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46600-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46600-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46600-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46600-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46600-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
