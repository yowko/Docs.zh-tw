---
title: ICorDebugSymbolProvider 介面
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9f475ee3c46b8abb94ce7f804cc8b4a8054ec2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider 介面
提供可用來擷取偵錯符號資訊的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyImageBytes 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|如果合併組件中有相對虛擬位址 (RVA)，則會從合併組件讀取資料。|  
|[GetAssemblyImageMetadata 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|從合併組件傳回中繼資料。|  
|[GetCodeRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|提供方法中的相對虛擬位址 (RVA)，以取得方法起始位址和大小。|  
|[GetInstanceFieldSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|取得對應 TypeSpec 簽章的執行個體欄位符號。|  
|[GetMergedAssemblyRecords 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|取得所有合併組件的符號記錄。|  
|[GetMethodLocalSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|提供方法的相對虛擬位址 (RVA)，取得該方法的本機符號。|  
|[GetMethodParameterSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|提供方法的相對虛擬位址 (RVA)，取得該方法的參數符號。|  
|[GetMethodProps 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|傳回方法屬性的相關資訊，例如方法的中繼資料語彙基元，以及其泛型參數的相關資訊 (假設該方法中有相對虛擬位址 (RVA))。|  
|[GetObjectSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|傳回根據某物件之 typespec 簽章的該物件大小。|  
|[GetStaticFieldSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|取得對應至 TypeSpec 簽章的靜態欄位符號。|  
|[GetTypeProps 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|根據 vtable 中指定的相對虛擬位址 (RVA)，傳回類型之屬性的相關資訊，例如其泛型參數的簽章數目。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
