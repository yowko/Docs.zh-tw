---
title: ICLRTaskManager::GetCurrentTaskType 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728780"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a>ICLRTaskManager::GetCurrentTaskType 方法

取得目前正在執行之工作的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a>參數  

 `pTaskType`  
 擴展 [ETaskType](etasktype-enumeration.md) 列舉值的指標，指出目前正在執行的工作類型。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
