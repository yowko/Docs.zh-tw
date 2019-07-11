---
title: AddFile 方法
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ff6bde5009e834bfca156fe4d3ad16da53ded85
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742379"
---
# <a name="addfile-method"></a>AddFile 方法
將檔案加入至組件。 也可以用來建立未繫結的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 要當做引數的組件的唯一識別碼。  
  
 `pszFilename`  
 要加入檔案的完整的名稱。  
  
 `dwFlags`  
 COM + FileDef 加上旗標這類`ffContainsNoMetaData`和`ffWriteable`。 `dwFlags` 傳遞給[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pEmitter`  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)來發出中繼資料，如有必要的介面。  
  
 `pFileToken`  
 若要加入的檔案的唯一識別碼的儲存位置的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
