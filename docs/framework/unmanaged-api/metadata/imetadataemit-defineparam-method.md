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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431696"
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
 在參數的旗標。 這是 `CorParamAttr` 值的位元遮罩。  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_`常數值的 *\** 。  
  
 `pValue`  
 在參數的常數值。  
  
 `cchValue`  
 在`pValue`的大小，以 Unicode 字元為單位。  
  
 `ppd`  
 脫銷指派的 `mdParamDef` token。  
  
## <a name="remarks"></a>備註  
 `ulParamSeq` 中的順序值會以1為參數開頭。 傳回值的序號為0。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
