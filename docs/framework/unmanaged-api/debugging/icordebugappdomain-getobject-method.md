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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895216"
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
 如果尚未針對<xref:System.AppDomain?displayProperty=nameWithType>這個應用程式域建立 managed 物件，則方法會傳回`S_FALSE` ，並`NULL`將`*ppObject`位置放入中。  
  
## <a name="remarks"></a>備註  
 進程中的每個應用程式域在代表<xref:System.AppDomain?displayProperty=nameWithType>它的執行時間中可能會有一個 managed 物件。 此函式會取得對應至這個 managed <xref:System.AppDomain?displayProperty=nameWithType>物件的 ICorDebugValue 介面物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
