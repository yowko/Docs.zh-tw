---
title: IMetaDataImport::EnumPermissionSets 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: eef2c733f96d74e3353a940cc90f1a631cf48a36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690492"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets 方法

列舉指定中繼資料範圍內的物件權限。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標。 此方法的第一個呼叫必須是 Null。  
  
 `tk`  
 在限制搜尋範圍的元資料標記，或 Null 表示盡可能搜尋最廣泛的範圍。  
  
 `dwActions`  
 在旗標 <xref:System.Security.Permissions.SecurityAction> ，代表要包含在中的值 `rPermission` ，或零表示傳回所有動作。  
  
 `rPermission`  
 擴展用來儲存許可權權杖的陣列。  
  
 `cMax`  
 [in] `rPermission` 陣列的大小上限。  
  
 `pcTokens`  
 擴展中傳回的許可權權杖數目 `rPermission` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets` 傳回成功。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTokens` 是零。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
