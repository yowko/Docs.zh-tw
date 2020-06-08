---
title: IMetaDataEmit2::DefineGenericParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503805"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam 方法
建立泛型型別參數的定義，並取得該泛型型別參數的 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在`mdTypeDef`或 `mdMethodDef` token，表示要定義泛型參數的方法或構造函式。  
  
 `ulParamSeq`  
 在泛型參數的索引。  
  
 `dwParamFlags`  
 在[CorGenericParamAttr](corgenericparamattr-enumeration.md)列舉的值，描述泛型參數的類型。  
  
 `szname`  
 在參數的名稱。  
  
 `reserved`  
 在此參數保留供未來擴充性之用。  
  
 `rtkConstraints`  
 在類型條件約束之以零結束的陣列。 陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。  
  
 `pgp`  
 脫銷表示泛型參數的 token。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
