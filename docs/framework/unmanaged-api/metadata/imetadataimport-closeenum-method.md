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
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492470"
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
 在要關閉之枚舉器的控制碼。  
  
## <a name="remarks"></a>備註  
 所指定的控制碼 `hEnum` 是從先前的 `Enum` *名稱*呼叫取得（例如， [IMetaDataImport：： EnumTypeDefs](imetadataimport-enumtypedefs-method.md)）。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
