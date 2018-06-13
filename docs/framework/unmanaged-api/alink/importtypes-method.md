---
title: ImportTypes 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321038a148c27086ca499e2f448eb50cb93525ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405508"
---
# <a name="importtypes-method"></a>ImportTypes 方法
起始從透過匯入每個範圍的型別匯入[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 若要匯入的組件識別碼。  
  
 `FileToken`  
 要從匯入的檔案識別碼。  
  
 `dwScope`  
 若要匯入的以零為起始範圍。  
  
 `phEnum`  
 在此範圍內接收列舉值類型的控制代碼。  
  
 `ppImportScope`  
 選擇性地接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面。  
  
 `pdwCountOfTypes`  
 選擇性地指定範圍內接收類型的計數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
