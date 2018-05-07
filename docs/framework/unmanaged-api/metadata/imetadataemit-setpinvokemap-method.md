---
title: IMetaDataEmit::SetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84b2c0571a7991829e65b45759bd61fa4009aa71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap 方法
設定或變更在先前呼叫所定義的功能，該方法的 PInvoke 簽章， [imetadataemit:: Definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a>參數  
 `tk`  
 [in]`mdToken`資訊套用到對應。  
  
 `dwMappingFlags`  
 [in]用來執行對應 PInvoke 旗標。 這是位元遮罩`CorPinvokeMap`值。  
  
 `szImportName`  
 [in]原生 DLL 中匯出目標的名稱。  
  
 `mrImportDLL`  
 [in]`mdModuleRef`權杖的目標 unmanaged DLL。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
