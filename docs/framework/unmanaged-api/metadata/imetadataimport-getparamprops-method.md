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
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491052"
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
 在所要求的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷傳回的大小（以寬字元為單位） `szName` 。  
  
 `pdwAttr`  
 脫銷與參數相關聯之任何屬性旗標的指標。 這是值的位元遮罩 `CorParamAttr` 。  
  
 `pdwCPlusTypeFlag`  
 脫銷指定參數為之旗標的指標 <xref:System.ValueType> 。  
  
 `ppValue`  
 脫銷參數所傳回之常數位串的指標。  
  
 `pcchValue`  
 脫銷的大小 `ppValue` ，以寬字元為單位，如果 `ppValue` 不包含字串，則為零。  
  
## <a name="remarks"></a>備註

參數的順序值 `pulSequence` 開頭為1。 傳回值的序號為0。

## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
