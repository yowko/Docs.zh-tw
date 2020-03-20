---
title: IMetaDataEmit::SetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177557"
---
# <a name="imetadataemitsetfieldprops-method"></a>IMetaDataEmit::SetFieldProps 方法
設置或更新指定欄位權杖引用的欄位的預設值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>參數  
 `fd`  
 [在]目標欄位的權杖。  
  
 `dwFieldFlags`  
 [在]欄位屬性。 這是值的`CorFieldAttr`位元遮罩。  
  
 `dwCPlusTypeFlag`  
 [在]常`ELEMENT_TYPE_`*\** 量值的 。 這是一個`CorElementType`值。 如果未定義常量，則將此值設置為`ELEMENT_TYPE_END`。  
  
 `pValue`  
 [在]欄位的常量值。  
  
 `cchValue`  
 [在]的大小（以 Unicode 字元表示`pValue`）  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
