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
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805045"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager 介面
提供的方法可讓主機指定通用語言執行時間（CLR）或主機應載入的元件集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyStore 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|取得[IHostAssemblyStore](ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。|  
|[GetNonHostStoreAssemblies 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|取得[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)的介面指標，表示主機預期 CLR 載入的元件清單。|  
  
## <a name="remarks"></a>備註  
 不需要主機來執行 `IHostAssemblyManager` 或 `IHostAssemblyStore` 。 如果主機確實執行 `IHostAssemblyManager` ，它也必須執行 `IHostAssemblyStore` 。  
  
 執行時間會 `IHostAssemblyManager` 在初始化時呼叫[IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md) ，並使用 `IID` IID_IHostAssemblyManager 的來查詢。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
