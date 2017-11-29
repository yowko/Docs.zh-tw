---
title: "IMetaDataImport::GetClassLayout 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cece37a6321fc68cbff2957f9753af5f2f916f5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
