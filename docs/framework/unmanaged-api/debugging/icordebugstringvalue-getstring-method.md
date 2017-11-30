---
title: "ICorDebugStringValue::GetString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue.GetString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 077f8488419cee434a8dc8266b0814dfd4196b03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="92455-102">ICorDebugStringValue::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="92455-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="92455-103">取得此 ICorDebugStringValue 所參考的字串。</span><span class="sxs-lookup"><span data-stu-id="92455-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92455-104">語法</span><span class="sxs-lookup"><span data-stu-id="92455-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92455-105">參數</span><span class="sxs-lookup"><span data-stu-id="92455-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="92455-106">[in] `szString` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="92455-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="92455-107">[out]傳入的字元數的指標`szString`陣列。</span><span class="sxs-lookup"><span data-stu-id="92455-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="92455-108">[out]陣列，其中會儲存擷取的字串。</span><span class="sxs-lookup"><span data-stu-id="92455-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92455-109">需求</span><span class="sxs-lookup"><span data-stu-id="92455-109">Requirements</span></span>  
 <span data-ttu-id="92455-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92455-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92455-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92455-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92455-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92455-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92455-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92455-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
