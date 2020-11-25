---
title: IMetaDataImport::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: f418b48f1b62ae8093197d64ca44b2ef659990a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701714"
---
# <a name="imetadataimportcloseenum-method"></a>IMetaDataImport::CloseEnum 方法

關閉指定之控制碼所識別的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a>參數  

 `hEnum`  
 在要關閉之列舉值的控制碼。  
  
## <a name="remarks"></a>備註  

 指定的控制碼 `hEnum` 是從先前的 `Enum` *名稱* 呼叫取得 (例如， [IMetaDataImport：： EnumTypeDefs](imetadataimport-enumtypedefs-method.md)) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
