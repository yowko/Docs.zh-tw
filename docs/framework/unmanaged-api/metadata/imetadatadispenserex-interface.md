---
title: IMetaDataDispenserEx 介面
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431140"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx 介面
Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindAssembly 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|這個方法尚未實作。 If called, it returns E_NOTIMPL.|  
|[FindAssemblyModule 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|這個方法尚未實作。 If called, it returns E_NOTIMPL.|  
|[GetCORSystemDirectory 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Gets the directory that holds the current common language runtime (CLR). This method is supported only for use by out-of-process debuggers. If called from another component, it will return E_NOTIMPL.|  
|[GetOption 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Gets the value of the specified option for the current metadata scope. The option controls how calls to the current metadata scope are handled.|  
|[OpenScopeOnITypeInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|這個方法尚未實作。 If called, it returns E_NOTIMPL.|  
|[SetOption 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Sets the specified option to a given value for the current metadata scope. The option controls how calls to the current metadata scope are handled.|  
  
## <a name="requirements"></a>需求  
 **Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
