---
title: IMetaDataEmit::DefineParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177698"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam 方法
為指定權杖引用的方法創建具有指定簽名的參數定義，並獲取該參數定義的權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a>參數  
 `md`  
 [在]正在定義其參數的方法的權杖。  
  
 `ulParamSeq`  
 [在]參數序號。  
  
 `szName`  
 [在]Unicode 中參數的名稱。  
  
 `dwParamFlags`  
 [在]參數的標誌。 這是值的`CorParamAttr`位元遮罩。  
  
 `dwCPlusTypeFlag`  
 [在]`ELEMENT_TYPE_` *\**  
  
 `pValue`  
 [在]參數的常量值。  
  
 `cchValue`  
 [在]的大小（以 Unicode 字元表示`pValue`）  
  
 `ppd`  
 [出]分配的`mdParamDef`權杖。  
  
## <a name="remarks"></a>備註  
 中的序列值以`ulParamSeq`1 開頭的參數。 傳回值的序號為 0。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
