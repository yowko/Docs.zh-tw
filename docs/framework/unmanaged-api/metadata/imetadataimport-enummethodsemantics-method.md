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
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720967"
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
 [in，out]列舉值的指標。 此方法的第一個呼叫必須是 Null。  
  
 `mb`  
 在限制列舉範圍的 MethodDef 標記。  
  
 `rEventProp`  
 擴展用來儲存事件或屬性的陣列。  
  
 `cMax`  
 [in] `rEventProp` 陣列的大小上限。  
  
 `pcEventProp`  
 擴展中傳回的事件或屬性數目 `rEventProp` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` 傳回成功。|  
|`S_FALSE`|沒有要列舉的事件或屬性。 在此情況下， `pcEventProp` 是零。|  
  
## <a name="remarks"></a>備註  

 許多通用語言執行時間類型會定義與屬性相關的 *屬性* `Changed` 事件和 `On` *屬性* `Changed` 方法。 例如，型別會 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 定義 <xref:System.Windows.Forms.Control.Font%2A> 屬性、 <xref:System.Windows.Forms.Control.FontChanged> 事件和 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法。 屬性的 set 存取子方法會 <xref:System.Windows.Forms.Control.Font%2A> 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 方法，而這個方法接著會引發 <xref:System.Windows.Forms.Control.FontChanged> 事件。 您可以 `EnumMethodSemantics` 使用的 MethodDef 呼叫 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 來取得 <xref:System.Windows.Forms.Control.Font%2A> 屬性和事件的參考 <xref:System.Windows.Forms.Control.FontChanged> 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
