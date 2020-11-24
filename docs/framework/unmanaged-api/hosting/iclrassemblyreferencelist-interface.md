---
title: ICLRAssemblyReferenceList 介面
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679178"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList 介面

管理通用語言執行時間 (CLR) 載入的元件清單，而不是由主控制項所載入。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IsAssemblyReferenceInList 方法](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|取得值，這個值會指出提供的指標是否參考清單中的元件。|  
|[IsStringAssemblyReferenceInList 方法](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|取得值，這個值會指出提供的名稱是否符合清單中的元件名稱。|  
  
## <a name="remarks"></a>備註  

 呼叫 [ICLRAssemblyIdentityManager：： GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) 方法，以取得實例的指標 `ICLRAssemblyReferenceList` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
- [裝載介面](hosting-interfaces.md)
