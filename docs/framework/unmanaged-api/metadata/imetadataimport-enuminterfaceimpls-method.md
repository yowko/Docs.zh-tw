---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 0b040a2741a44b9d361dabc38c26b8934659003b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711516"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法

列舉由指定的所執行的所有介面 `TypeDef` 。
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標。  
  
 `td`  
 在要列舉其 MethodDef token 表示介面實作為的 TypeDef 標記。  
  
 `rImpls`  
 擴展用來儲存 MethodDef 標記的陣列。  
  
 `cMax`  
 在陣列的最大長度 `rImpls` 。  
  
 `pcImpls`  
 擴展在中傳回的實際標記數目 `rImpls` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` 傳回成功。|  
|`S_FALSE`|沒有要列舉的 MethodDef 標記。 在此情況下， `pcImpls` 會設定為零。|  

## <a name="remarks"></a>備註

列舉會傳回 `mdInterfaceImpl` 所指定的每個介面的標記集合 `TypeDef` 。 介面標記會依照 (透過或) 指定介面的順序傳回 `DefineTypeDef` `SetTypeDefProps` 。 您 `mdInterfaceImpl` 可以使用 [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)來查詢所傳回權杖的屬性。
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
