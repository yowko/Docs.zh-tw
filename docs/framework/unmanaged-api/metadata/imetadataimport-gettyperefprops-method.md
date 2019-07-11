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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4d8829c9cb2818eafe98809c9a0d5fd8109d076
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778829"
---
# <a name="imetadataimportgettyperefprops-method"></a>IMetaDataImport::GetTypeRefProps 方法
取得相關聯的中繼資料<xref:System.Type>指定 TypeRef 語彙基元所參考。  
  
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
 [in]TypeRef 語彙基元，表示要傳回的中繼資料的型別。  
  
 `ptkResolutionScope`  
 [out]建立參考的範圍指標。 這個值會是一個 AssemblyRef 或 ModuleRef 語彙基元。  
  
 `szName`  
 [out]緩衝區，包含型別名稱。  
  
 `cchName`  
 [in]所要求的大小，以寬字元為單位的`szName`。  
  
 `pchName`  
 [out]寬字元在傳回的大小`szName`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
