---
title: GetScope2 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741836"
---
# <a name="getscope2-method"></a>GetScope2 方法
取得匯入範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 目標組件的識別碼。  
  
 `FileToken`  
 要從中匯入的檔案識別碼。  
  
 `dwScope`  
 若要匯入的以零為起始範圍。  
  
 `ppImportScope`  
 接收指標[IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)指定範圍的介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
