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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134707"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject 方法
取得 common language runtime （CLR）應用程式域的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppObject`  
 脫銷表示 CLR 應用程式域之 ICorDebugValue 介面物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果尚未為這個應用程式域建立 managed <xref:System.AppDomain?displayProperty=nameWithType> 物件，此方法會傳回 `S_FALSE`，並將 `NULL` 放在 `*ppObject`中。  
  
## <a name="remarks"></a>備註  
 進程中的每個應用程式域在代表它的執行時間中可能會有 managed <xref:System.AppDomain?displayProperty=nameWithType> 物件。 此函式會取得對應至這個 managed <xref:System.AppDomain?displayProperty=nameWithType> 物件的 ICorDebugValue 介面物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
