---
title: IAssemblyCache::CreateAssemblyScavenger 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyScavenger
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyScavenger
helpviewer_keywords:
- CreateAssemblyScavenger method [.NET Framework fusion]
- IAssemblyCache::CreateAssemblyScavanger method [.NET Framework fusion]
ms.assetid: e8bb98f1-e477-45d2-8956-ba404137cd2d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fe1857e0eb22ee75cda6f612fbc0e1c699a3bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428477"
---
# <a name="iassemblycachecreateassemblyscavenger-method"></a>IAssemblyCache::CreateAssemblyScavenger 方法
融合技術，以保留供內部使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateAssemblyScavenger (  
    [out] IUnknown **ppUnkReserved  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUnkReserved`  
 [out]傳回`IUnknown`指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IAssemblyCache 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
