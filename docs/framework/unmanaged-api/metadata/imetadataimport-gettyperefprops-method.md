---
title: IMetaDataImport::GetTypeRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 273922e00c3e5319d5a03652cc77b69f4479ea67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503519"
---
# <a name="imetadataimportgettyperefprops-method"></a>IMetaDataImport::GetTypeRefProps 方法
取得與指定的 TypeRef 標記所參考之相關聯的中繼資料 <xref:System.Type> 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a>參數  
 `tr`  
 在表示要傳回中繼資料之類型的 TypeRef token。  
  
 `ptkResolutionScope`  
 脫銷做為參考之範圍的指標。 這個值是 AssemblyRef 或 ModuleRef token。  
  
 `szName`  
 脫銷包含型別名稱的緩衝區。  
  
 `cchName`  
 在所要求的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷傳回的大小（以寬字元為單位） `szName` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
