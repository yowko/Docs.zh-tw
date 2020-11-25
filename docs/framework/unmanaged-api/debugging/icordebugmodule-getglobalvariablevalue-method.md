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
ms.openlocfilehash: 94fe7deb10c23ea0bc824bb2244e8d1d87f831e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710022"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="b1b2a-102">ICorDebugModule::GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="b1b2a-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>

<span data-ttu-id="b1b2a-103">取得指定之全域變數的值。</span><span class="sxs-lookup"><span data-stu-id="b1b2a-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1b2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1b2a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1b2a-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="b1b2a-106">在 `mdFieldDef` 參考描述全域變數之中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="b1b2a-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b1b2a-107">擴展ICorDebugValue 物件位址的指標，該物件表示指定之全域變數的值。</span><span class="sxs-lookup"><span data-stu-id="b1b2a-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b2a-108">需求</span><span class="sxs-lookup"><span data-stu-id="b1b2a-108">Requirements</span></span>  

 <span data-ttu-id="b1b2a-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1b2a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b2a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1b2a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1b2a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1b2a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1b2a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
