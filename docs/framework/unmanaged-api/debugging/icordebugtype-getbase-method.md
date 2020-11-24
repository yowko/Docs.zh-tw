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
ms.openlocfilehash: 967f8f25e240f484ae86852c740be12cd3a6409e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681817"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="8e2d2-102">ICorDebugType::GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="8e2d2-102">ICorDebugType::GetBase Method</span></span>

<span data-ttu-id="8e2d2-103">取得 ICorDebugType 的介面指標，該指標表示這個所表示之型別的基底型別（如果有的話） `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="8e2d2-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e2d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e2d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e2d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e2d2-105">Parameters</span></span>  

 `pBase`  
 <span data-ttu-id="8e2d2-106">擴展 `ICorDebugType` 代表基底類型之物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8e2d2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e2d2-107">備註</span><span class="sxs-lookup"><span data-stu-id="8e2d2-107">Remarks</span></span>  

 <span data-ttu-id="8e2d2-108">查閱類型的基底類型，對於執行常見的偵錯工具功能很有用，例如列印出物件或其父類別的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="8e2d2-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e2d2-109">需求</span><span class="sxs-lookup"><span data-stu-id="8e2d2-109">Requirements</span></span>  

 <span data-ttu-id="8e2d2-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e2d2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e2d2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e2d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e2d2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e2d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e2d2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e2d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
