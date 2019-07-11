---
title: SetAssemblyFile2 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d96881ce35dca1ee7a196507ef8d81a565eed82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741510"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 方法
設定的名稱和新的組件的選項。 當您產生未繫結的模組時，請勿呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFilename`  
 資訊清單檔案的名稱。  
  
 `pEmitter`  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面，此檔案。  
  
 `afFlags`  
 所表示的選項[AssemblyFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。  
  
 `pAssemblyID`  
 接收所建構的組件的唯一識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
