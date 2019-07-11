---
title: GetFileDef 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a51e8c83d0949f68a41f6a4e10396adbc4f3c9c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741886"
---
# <a name="getfiledef-method"></a>GetFileDef 方法
擷取中繼資料 （而不是由 ALink 指派的權杖） 中所使用的實際 FileDef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 組件的識別碼。  
  
 `TargetFile`  
 語彙基元的加入的檔案從 AddFile 方法或 AddImport 方法擷取。  
  
 `pScope`  
 接收 FileDef 語彙基元。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
