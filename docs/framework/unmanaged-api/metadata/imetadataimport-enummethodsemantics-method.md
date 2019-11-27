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
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450071"
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
 [in、out]列舉值的指標。 第一次呼叫此方法時，此值必須為 Null。  
  
 `mb`  
 在會限制列舉範圍的 MethodDef token。  
  
 `rEventProp`  
 脫銷用來儲存事件或屬性的陣列。  
  
 `cMax`  
 [in] `rEventProp` 陣列的大小上限。  
  
 `pcEventProp`  
 脫銷`rEventProp`中傳回的事件或屬性數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumMethodSemantics`。|  
|`S_FALSE`|沒有要列舉的事件或屬性。 在此情況下，`pcEventProp` 為零。|  
  
## <a name="remarks"></a>備註  
 許多通用語言執行時間型別會定義*屬性*`Changed` 事件，以及與屬性相關的 `On`*屬性*`Changed` 方法。 例如，<xref:System.Windows.Forms.Control?displayProperty=nameWithType> 型別會定義 <xref:System.Windows.Forms.Control.Font%2A> 屬性、<xref:System.Windows.Forms.Control.FontChanged> 事件和 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法。 <xref:System.Windows.Forms.Control.Font%2A> 屬性的 set 存取子方法會呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法，進而引發 <xref:System.Windows.Forms.Control.FontChanged> 事件。 您會使用 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 的 MethodDef 來呼叫 `EnumMethodSemantics`，以取得 <xref:System.Windows.Forms.Control.Font%2A> 屬性和 <xref:System.Windows.Forms.Control.FontChanged> 事件的參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
