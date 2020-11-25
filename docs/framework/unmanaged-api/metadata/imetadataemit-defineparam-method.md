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
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719524"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam 方法

針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的標記。  
  
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
 在要定義其參數之方法的標記。  
  
 `ulParamSeq`  
 在參數序號。  
  
 `szName`  
 在Unicode 中參數的名稱。  
  
 `dwParamFlags`  
 在參數的旗標。 這是值的位元遮罩 `CorParamAttr` 。  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** 做為常數值。  
  
 `pValue`  
 在參數的常數值。  
  
 `cchValue`  
 在的大小（以 Unicode 字元為單位） `pValue` 。  
  
 `ppd`  
 擴展 `mdParamDef` 指派的權杖。  
  
## <a name="remarks"></a>備註  

 參數開頭為1的順序值 `ulParamSeq` 。 傳回值的序號為0。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
