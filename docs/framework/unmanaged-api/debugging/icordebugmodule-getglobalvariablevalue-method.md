---
title: "ICorDebugModule::GetGlobalVariableValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetGlobalVariableValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00fb56353652e2fdeac7d7b42c030d9105cc9aca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="dc96b-102">ICorDebugModule::GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="dc96b-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="dc96b-103">取得指定的全域變數的值。</span><span class="sxs-lookup"><span data-stu-id="dc96b-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc96b-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc96b-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc96b-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc96b-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="dc96b-106">[in]`mdFieldDef`參考描述全域變數的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dc96b-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dc96b-107">[out]ICorDebugValue 物件，代表指定之全域變數值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="dc96b-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc96b-108">需求</span><span class="sxs-lookup"><span data-stu-id="dc96b-108">Requirements</span></span>  
 <span data-ttu-id="dc96b-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc96b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc96b-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc96b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc96b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc96b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc96b-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc96b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
