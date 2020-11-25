---
title: IMetaDataImport2::GetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 16f69d571ffed87a2e848124ce16ac942d319c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702676"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps 方法

取得與指定標記所表示之泛型參數相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>參數  

 `gp`  
 在代表要傳回中繼資料之泛型參數的 token。  
  
 `pulParamSeq`  
 擴展 `Type` 參數在父函式或方法中的序數位置。  
  
 `pdwParamFlags`  
 擴展描述泛型參數之的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 列舉值 `Type` 。  
  
 `ptOwner`  
 擴展代表參數擁有者的 TypeDef 或 MethodDef token。  
  
 `reserved`  
 擴展保留供未來擴充性之用。  
  
 `wzName`  
 擴展泛型參數的名稱。  
  
 `cchName`  
 在緩衝區的大小 `wzName` 。  
  
 `pchName`  
 擴展傳回的名稱大小（以寬字元為單位）。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
