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
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491455"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName 方法
取得自訂屬性，並指定其名稱和擁有者。  
  
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
 在元資料標記，代表擁有自訂屬性的物件。  
  
 `szName`  
 在自訂屬性的名稱。  
  
 `ppData`  
 脫銷資料陣列的指標，這是自訂屬性的值。  
  
 `pcbData`  
 脫銷傳回的資料大小（以位元組為單位） * `ppData` 。  
  
## <a name="remarks"></a>備註  
 為相同擁有者定義多個自訂屬性是合法的：他們甚至可能會有相同的名稱。 不過， `GetCustomAttributeByName` 只會傳回一個實例。 （傳回 `GetCustomAttributeByName` 第一個遇到的實例）。若要尋找自訂屬性的所有實例，請呼叫[IMetaDataImport：： EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md)方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
