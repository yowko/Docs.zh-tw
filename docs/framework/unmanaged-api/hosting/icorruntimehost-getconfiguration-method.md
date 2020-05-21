---
title: ICorRuntimeHost::GetConfiguration 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762262"
---
# <a name="icorruntimehostgetconfiguration-method"></a>ICorRuntimeHost::GetConfiguration 方法
取得物件，可讓主機指定 common language runtime （CLR）的回呼設定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a>參數  
 `pConfiguration`  
 脫銷[ICorConfiguration](icorconfiguration-interface.md)物件位址的指標，可用於設定 CLR。  
  
## <a name="remarks"></a>備註  
 CLR 必須在初始化之前設定;否則，此 `GetConfiguration` 方法會傳回 HRESULT，指出發生錯誤。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
