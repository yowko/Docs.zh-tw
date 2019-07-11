---
title: ICorDebugAppDomain::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1201ac0dca9cbd48c24b2621eba079ae672fd310
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737851"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject 方法
Common language runtime (CLR) 應用程式定義域中取得的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppObject`  
 [out]ICorDebugValue 介面物件，表示 CLR 應用程式定義域的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果 managed<xref:System.AppDomain?displayProperty=nameWithType>尚未針對這個應用程式定義域已建構物件，此方法會傳回`S_FALSE`，並將放`NULL`在`*ppObject`。  
  
## <a name="remarks"></a>備註  
 每個應用程式定義域的處理序中可能有 managed<xref:System.AppDomain?displayProperty=nameWithType>表示該執行階段中的物件。 此函式取得 ICorDebugValue 介面物件，對應至這個受控<xref:System.AppDomain?displayProperty=nameWithType>物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
