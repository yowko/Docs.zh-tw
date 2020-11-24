---
title: IHostAssemblyStore 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: 4b2fed963d2d0ebec54e5f7a4d95cba26c1bac1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680934"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore 介面

提供可讓主機獨立載入元件和模組的方法， (CLR) 的通用語言執行時間。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ProvideAssembly 方法](ihostassemblystore-provideassembly-method.md)|取得元件的參考，該元件不是由呼叫[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)所傳回的[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)所參考。|  
|[ProvideModule 方法](ihostassemblystore-providemodule-method.md)|解析元件內的模組，或未內嵌) 資源檔的連結 (。|  
  
## <a name="remarks"></a>備註  

 `IHostAssemblyStore` 提供一種方式，讓主機根據元件身分識別有效率地載入元件。 主機會藉由傳回 `IStream` 直接指向位元組的實例來載入元件。  
  
 CLR 會透過在 `IHostAssemblyStore` 初始化時呼叫來判斷主機是否已執行 `IHostAssemblyManager::GetNonHostAssemblyStores` 。 例如，這可讓主機控制使用者元件的系結，但是依賴執行時間系結至 .NET Framework 元件。  
  
> [!NOTE]
> 在提供的執行中 `IHostAssemblyStore` ，主機會指定其意圖，以解析從傳回之所參考的所有元件 `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` 。  
  
> [!NOTE]
> .NET Framework 版本2.0 未提供方法讓主機載入元件的原生映射，如 [原生映射產生器 ( # A0) ](../../tools/ngen-exe-native-image-generator.md) 公用程式所提供。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
