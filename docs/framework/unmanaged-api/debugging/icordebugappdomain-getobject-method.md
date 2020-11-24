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
ms.openlocfilehash: a163667ea7eca1ed817d642efdb8fc4efa2a0651
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676058"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject 方法

取得 common language runtime (CLR) 應用程式域的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppObject`  
 擴展ICorDebugValue 介面物件位址的指標，該物件代表 CLR 應用程式域。  
  
## <a name="return-value"></a>傳回值  

 如果 <xref:System.AppDomain?displayProperty=nameWithType> 尚未針對這個應用程式域來建立 managed 物件，則方法會傳回 `S_FALSE` 並放 `NULL` 入 `*ppObject` 。  
  
## <a name="remarks"></a>備註  

 進程中的每個應用程式域在執行時間中可能會有 <xref:System.AppDomain?displayProperty=nameWithType> 代表它的 managed 物件。 此函式會取得對應至此 managed 物件的 ICorDebugValue 介面物件 <xref:System.AppDomain?displayProperty=nameWithType> 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
