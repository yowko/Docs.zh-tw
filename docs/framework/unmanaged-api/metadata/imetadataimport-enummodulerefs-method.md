---
title: IMetaDataImport::EnumModuleRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491741"
---
# <a name="imetadataimportenummodulerefs-method"></a>IMetaDataImport::EnumModuleRefs 方法
列舉代表已匯入的模組之 ModuleRef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。 第一次呼叫此方法時，此值必須為 Null。  
  
 `rModuleRefs`  
 脫銷用來儲存 ModuleRef 標記的陣列。  
  
 `cMax`  
 [in] `rModuleRefs` 陣列的大小上限。  
  
 `pcModuleRefs`  
 脫銷在中傳回的 ModuleRef token 數目 `rModuleRefs` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumModuleRefs`已成功傳回。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcModuleRefs` 是零。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
