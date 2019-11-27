---
title: IMetaDataImport::GetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437120"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps 方法
取得指定 ParamDef 語彙基元所參考參數的中繼資料值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在ParamDef token，表示要傳回中繼資料的參數。  
  
 `pmd`  
 脫銷MethodDef token 的指標，代表接受參數的方法。  
  
 `pulSequence`  
 脫銷方法引數清單中參數的序數位置。  
  
 `szName`  
 脫銷保存參數名稱的緩衝區。  
  
 `cchName`  
 在要求的大小，以 `szName`的寬字元為單位。  
  
 `pchName`  
 脫銷`szName`的寬字元傳回大小。  
  
 `pdwAttr`  
 脫銷與參數相關聯之任何屬性旗標的指標。 這是 `CorParamAttr` 值的位元遮罩。  
  
 `pdwCPlusTypeFlag`  
 脫銷旗標的指標，指定參數為 <xref:System.ValueType>。  
  
 `ppValue`  
 脫銷參數所傳回之常數位串的指標。  
  
 `pcchValue`  
 脫銷`ppValue` 的大小，以寬字元為單位，如果 `ppValue` 不包含字串，則為零。  
  
## <a name="remarks"></a>備註

`pulSequence` 中的順序值會以1為參數開頭。 傳回值的序號為0。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
