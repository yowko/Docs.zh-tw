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
ms.openlocfilehash: a58e03875ec021b41479085fa9e27a4321ae965e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004344"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam 方法
針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的 token。  
  
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
 在要定義其參數之方法的 token。  
  
 `ulParamSeq`  
 在參數序號。  
  
 `szName`  
 在Unicode 中的參數名稱。  
  
 `dwParamFlags`  
 在參數的旗標。 這是值的位元遮罩 `CorParamAttr` 。  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** 作為常數值。  
  
 `pValue`  
 在參數的常數值。  
  
 `cchValue`  
 在的大小，以 Unicode 字元為單位 `pValue` 。  
  
 `ppd`  
 脫銷`mdParamDef`指派的 token。  
  
## <a name="remarks"></a>備註  
 參數的順序值 `ulParamSeq` 開頭為1。 傳回值的序號為0。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
