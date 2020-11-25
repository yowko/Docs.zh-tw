---
title: IMetaDataImport::GetMethodSemantics 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: cc01a417c3246ad2554c506f21e37a3cbbdeb991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733177"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics 方法

取得旗標，指出指定的 MethodDef 標記所參考的方法與指定之 EventProp token 所參考的成對屬性和事件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `mb`  
 在代表取得之語義角色資訊之方法的 MethodDef 標記。  
  
 `tkEventProp`  
 在Token，代表要取得方法角色的配對屬性和事件。  
  
 `pdwSemanticsFlags`  
 擴展相關聯之語義旗標的指標。 這個值是 [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) 列舉的位元遮罩。  
  
## <a name="remarks"></a>備註  

 [IMetaDataEmit：:D efineproperty](imetadataemit-defineproperty-method.md)方法會設定方法的語義旗標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
