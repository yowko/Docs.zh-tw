---
title: ICorDebugAppDomain::IsAttached 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0412089fee27e556c2f9230e9b34de3391b9bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402557"
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached 方法
取得值，指出是否要將偵錯工具附加至應用程式定義域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbAttached`  
 [out]`true`偵錯工具是否附加至應用程式定義域，否則`false`。  
  
## <a name="remarks"></a>備註  
 ICorDebugController 方法無法使用，直到偵錯工具附加至應用程式定義域。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
