---
title: IMetaDataDispenser::DefineScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11382f00839917185ba3c85b8fbae5c32d0b0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448606"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope 方法
您可以在其中建立新的中繼資料的記憶體中建立新的區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 [in]建立版本之中繼資料結構的 CLSID。 此值必須是 CLSID_CorMetaDataRuntime 適用於.NET Framework 2.0 版。  
  
 `dwCreateFlags`  
 [in]指定選項的旗標。 此值必須是針對.NET Framework 2.0 的零。  
  
 `riid`  
 [in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來建立新的中繼資料。  
  
 值`riid`必須指定其中一個 「 發出"介面。 有效值為 IID_IMetaDataEmit、 IID_IMetaDataAssemblyEmit 或 IID_IMetaDataEmit2。  
  
 `ppIUnk`  
 [out]要傳回的介面的指標。  
  
## <a name="remarks"></a>備註  
 `DefineScope` 建立一組的記憶體中中繼資料表，會產生唯一的 GUID （模組版本識別碼或 MVID） 的中繼資料，而且模組資料表中建立項目編譯單位所發出的。  
  
 您可以將屬性附加至中繼資料範圍為整個使用[imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)或[imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)方法，視需要。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
