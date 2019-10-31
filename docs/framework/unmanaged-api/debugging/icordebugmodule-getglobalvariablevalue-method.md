---
title: ICorDebugModule::GetGlobalVariableValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: 3afefdc3d704044184ea20d061eb9449458b5060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129570"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="2ad69-102">ICorDebugModule::GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="2ad69-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="2ad69-103">取得指定之全域變數的值。</span><span class="sxs-lookup"><span data-stu-id="2ad69-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad69-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ad69-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ad69-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ad69-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="2ad69-106">在`mdFieldDef` token，參考描述全域變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2ad69-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2ad69-107">脫銷ICorDebugValue 物件位址的指標，表示指定之全域變數的值。</span><span class="sxs-lookup"><span data-stu-id="2ad69-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad69-108">需求</span><span class="sxs-lookup"><span data-stu-id="2ad69-108">Requirements</span></span>  
 <span data-ttu-id="2ad69-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad69-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ad69-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ad69-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ad69-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ad69-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ad69-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ad69-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
