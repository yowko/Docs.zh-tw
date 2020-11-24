---
title: IHostAssemblyManager 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: a06e7f13b6de9450aa2a81f28f591c0a3ce8db0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680981"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager 介面

提供的方法可讓主機指定 common language runtime (CLR) 或主機所載入的元件集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyStore 方法](ihostassemblymanager-getassemblystore-method.md)|取得 [IHostAssemblyStore](ihostassemblystore-interface.md) 的介面指標，該指標表示主機載入的元件清單。|  
|[GetNonHostStoreAssemblies 方法](ihostassemblymanager-getnonhoststoreassemblies-method.md)|取得 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 的介面指標，該指標表示主機預期 CLR 載入的元件清單。|  
  
## <a name="remarks"></a>備註  

 不需要主機來執行 `IHostAssemblyManager` 或 `IHostAssemblyStore` 。 如果主機確實執行 `IHostAssemblyManager` ，則它也必須執行 `IHostAssemblyStore` 。  
  
 執行時間會在 `IHostAssemblyManager` 初始化時呼叫 [IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md) ，並使用 IID_IHostAssemblyManager 來查詢 `IID` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
