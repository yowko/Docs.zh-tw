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
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008010"
---
# <a name="imetadataemitsetfieldprops-method"></a>IMetaDataEmit::SetFieldProps 方法
設定或更新指定欄位標記所參考之欄位的預設值。  
  
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
 在目標欄位的 token。  
  
 `dwFieldFlags`  
 在欄位屬性。 這是值的位元遮罩 `CorFieldAttr` 。  
  
 `dwCPlusTypeFlag`  
 在`ELEMENT_TYPE_` *\** 常數值的。 這是 `CorElementType` 值。 如果沒有定義常數，請將此值設定為 `ELEMENT_TYPE_END` 。  
  
 `pValue`  
 在欄位的常數值。  
  
 `cchValue`  
 在的大小，以 Unicode 字元為單位 `pValue` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
