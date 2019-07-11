---
title: IMetaDataImport::GetCustomAttributeByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bebf254110d9970ff3a99f948ff2e831ffb6b35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782443"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName 方法
取得自訂屬性，指定其名稱和擁有者。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>參數  
 `tkObj`  
 [in]表示擁有該自訂屬性的物件中繼資料語彙基元。  
  
 `szName`  
 [in]自訂屬性的名稱。  
  
 `ppData`  
 [out]做為自訂屬性的值之資料的陣列指標。  
  
 `pcbData`  
 [out]以位元組為單位的中傳回的資料大小 *`ppData`。  
  
## <a name="remarks"></a>備註  
 它是合法來定義多個自訂屬性之相同的擁有者;他們甚至可能擁有相同的名稱。 不過，`GetCustomAttributeByName`傳回只有一個執行個體。 (`GetCustomAttributeByName`傳回遇到的第一個執行個體。)若要尋找自訂屬性的所有執行個體，呼叫[imetadataimport:: Enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
