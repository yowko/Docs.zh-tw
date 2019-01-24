---
title: IAssemblyCache 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157cc9f5f520f376c0c055ab49b116bc7961f421
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641066"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache 介面
表示使用的全域組件快取融合技術。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateAssemblyCacheItem 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|取得新的參考[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)。|  
|[CreateAssemblyScavenger 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|融合技術，以保留供內部使用。|  
|[InstallAssembly 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|指定的組件安裝在全域組件快取中。|  
|[QueryAssemblyInfo 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|取得指定的組件的相關要求的資料。|  
|[UninstallAssembly 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|從全域組件快取，解除安裝指定的組件。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [全域組件快取](../../../../docs/framework/app-domains/gac.md)
