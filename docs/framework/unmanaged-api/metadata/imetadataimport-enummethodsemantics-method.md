---
title: IMetaDataImport::EnumMethodSemantics 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16cfa6df6251cd67860155cb8092e77a835eaaef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992416"
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
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。 首次呼叫這個方法，這必須是 NULL。  
  
 `mb`  
 [in]列舉的範圍限制 MethodDef 語彙基元。  
  
 `rEventProp`  
 [out]用來儲存事件或屬性的陣列。  
  
 `cMax`  
 [in] `rEventProp` 陣列的大小上限。  
  
 `pcEventProp`  
 [out]事件或傳入的屬性數目`rEventProp`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` 已成功傳回。|  
|`S_FALSE`|沒有任何事件或列舉的屬性。 在此情況下，`pcEventProp`為零。|  
  
## <a name="remarks"></a>備註  
 許多 common language runtime 類型定義*屬性*`Changed`事件並`On`*屬性*`Changed`方法與它們的屬性。 例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>型別會定義<xref:System.Windows.Forms.Control.Font%2A>屬性，<xref:System.Windows.Forms.Control.FontChanged>事件，和<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法。 Set 存取子方法<xref:System.Windows.Forms.Control.Font%2A>屬性呼叫<xref:System.Windows.Forms.Control.OnFontChanged%2A>方法，進而引發<xref:System.Windows.Forms.Control.FontChanged>事件。 您可以呼叫`EnumMethodSemantics`使用的 MethodDef<xref:System.Windows.Forms.Control.OnFontChanged%2A>來取得參考<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.Control.FontChanged>事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
