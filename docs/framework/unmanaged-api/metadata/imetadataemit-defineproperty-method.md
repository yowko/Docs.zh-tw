---
title: IMetaDataEmit::DefineProperty 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175781"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty 方法
使用指定的`get`和方法`set`訪問器為指定類型創建屬性定義，並獲取該屬性定義的權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]正在定義屬性的類或介面的權杖。  
  
 `szProperty`  
 [在]屬性的名稱。  
  
 `dwPropFlags`  
 [在]屬性標誌。  
  
 `pvSig`  
 [在]屬性簽名。  
  
 `cbSig`  
 [在]中的`pvSig`位元組計數。  
  
 `dwCPlusTypeFlag`  
 [在]屬性的預設值的類型。  
  
 `pValue`  
 [在]屬性的預設值。  
  
 `cchValue`  
 [在]中的（Unicode） 字元的`pValue`計數。  
  
 `mdSetter`  
 [在]設置屬性值的方法。  
  
 `mdGetter`  
 [在]獲取屬性值的方法。  
  
 `rmdOtherMethods[]`  
 [在]與 屬性關聯的其他方法的陣列。 使用 終止陣列`mdTokenNil`。  
  
 `pmdProp`  
 [出]分配的`mdProperty`權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
