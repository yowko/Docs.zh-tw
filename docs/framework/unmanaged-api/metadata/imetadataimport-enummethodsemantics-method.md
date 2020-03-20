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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175456"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics 方法
列舉和指定方法相關的屬性及屬性變更事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [進出]指向枚舉器的指標。 對於此方法的第一次調用，這必須為 Null。  
  
 `mb`  
 [在]限制枚舉範圍的 MethodDef 權杖。  
  
 `rEventProp`  
 [出]用於存儲事件或屬性的陣列。  
  
 `cMax`  
 [in] `rEventProp` 陣列的大小上限。  
  
 `pcEventProp`  
 [出]在 中`rEventProp`返回的事件或屬性數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`已成功返回。|  
|`S_FALSE`|沒有要枚舉的事件或屬性。 在這種情況下，`pcEventProp`為零。|  
  
## <a name="remarks"></a>備註  
 許多通用語言運行時類型定義與其屬性相關的*屬性*`Changed`事件和`On`*屬性*`Changed`方法。 例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>類型定義<xref:System.Windows.Forms.Control.Font%2A>屬性、<xref:System.Windows.Forms.Control.FontChanged>事件和方法。 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 屬性調用<xref:System.Windows.Forms.Control.Font%2A><xref:System.Windows.Forms.Control.OnFontChanged%2A>方法的集訪問器方法，該方法反過來引發事件<xref:System.Windows.Forms.Control.FontChanged>。 您將使用`EnumMethodSemantics`MethodDef 調用，<xref:System.Windows.Forms.Control.OnFontChanged%2A>以獲得對<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.Control.FontChanged>事件的引用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
