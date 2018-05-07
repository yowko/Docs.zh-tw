---
title: IMetaDataImport::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b031fc35a4687a8535e3cb5e9ef2a53bab9fe376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout 方法
取得指定 TypeDef 語彙基元所參考類別的配置資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]要傳回的版面配置類別的 TypeDef 語彙基元。  
  
 `pdwPackSize`  
 [out]其中一個值 1、 2、 4、 8 或 16，表示類別的組件的大小。  
  
 `rFieldOffset`  
 [out]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)值。  
  
 `cMax`  
 [in] `rFieldOffset` 陣列的大小上限。  
  
 `pcFieldOffset`  
 [out]傳回的項目數`rFieldOffset`。  
  
 `pulClassSize`  
 [out]大小 （位元組） 所表示的類別`td`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
