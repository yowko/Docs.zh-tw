---
title: "ICorDebugFunction::GetNativeCode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fccfaeb346d59f5cf565f47a9a64e732706adad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode 方法
取得原生程式碼的函式，由這個 ICorDebugFunction 執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCode`  
 [out]ICorDebugCode 執行個體，代表原生程式碼，此函式，或 null，如有此函式是 Microsoft intermediate language (MSIL) 程式碼尚未在 just-in-time (JIT) 編譯的指標。  
  
## <a name="remarks"></a>備註  
 如果這由函式`ICorDebugFunction`執行個體已被 JIT 編譯一次以上，如果是泛型型別，`GetNativeCode`傳回隨機的原生程式碼物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
