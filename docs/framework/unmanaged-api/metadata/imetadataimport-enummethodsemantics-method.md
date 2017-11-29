---
title: "IMetaDataImport::EnumMethodSemantics 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d5ec79701f73b8beb7759d72b972fc347a339c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics 方法
列舉和指定方法相關的屬性及屬性變更事件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。 這必須是 NULL 的第一個呼叫此方法。  
  
 `mb`  
 [in]列舉的範圍限制 MethodDef 語彙基元。  
  
 `rEventProp`  
 [out]用來儲存事件或屬性的陣列。  
  
 `cMax`  
 [in] `rEventProp` 陣列的大小上限。  
  
 `pcEventProp`  
 [out]事件或屬性中傳回的數目`rEventProp`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`已成功傳回。|  
|`S_FALSE`|沒有事件或列舉的屬性。 在此情況下，`pcEventProp`為零。|  
  
## <a name="remarks"></a>備註  
 許多 common language runtime 類型定義*屬性*`Changed`事件和`On`*屬性*`Changed`其屬性與相關方法。 比方說，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>型別定義<xref:System.Windows.Forms.Control.Font%2A>屬性，<xref:System.Windows.Forms.Control.FontChanged>事件，以及<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法。 Set 存取子方法的<xref:System.Windows.Forms.Control.Font%2A>屬性呼叫<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法，進而引發<xref:System.Windows.Forms.Control.FontChanged>事件。 您可以呼叫`EnumMethodSemantics`使用如 MethodDef<xref:System.Windows.Forms.Control.OnFontChanged%2A>取得參考<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.Control.FontChanged>事件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
