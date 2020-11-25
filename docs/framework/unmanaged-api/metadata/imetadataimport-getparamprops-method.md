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
ms.openlocfilehash: a16621f4c9b06f049239dc4e2335d70a167dd756
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729261"
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
 在代表要傳回之中繼資料之參數的 ParamDef token。  
  
 `pmd`  
 擴展MethodDef token 的指標，代表接受參數的方法。  
  
 `pulSequence`  
 擴展方法引數清單中參數的序數位置。  
  
 `szName`  
 擴展保存參數名稱的緩衝區。  
  
 `cchName`  
 在要求的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 擴展傳回的大小（以寬字元為單位） `szName` 。  
  
 `pdwAttr`  
 擴展與參數相關聯之任何屬性旗標的指標。 這是值的位元遮罩 `CorParamAttr` 。  
  
 `pdwCPlusTypeFlag`  
 擴展旗標的指標，指定參數為 <xref:System.ValueType> 。  
  
 `ppValue`  
 擴展參數所傳回之常數位符串的指標。  
  
 `pcchValue`  
 擴展的大小 `ppValue` （以寬字元為單位），如果不包含字串，則為零 `ppValue` 。  
  
## <a name="remarks"></a>備註

參數開頭為1的順序值 `pulSequence` 。 傳回值的序號為0。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
