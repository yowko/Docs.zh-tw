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
ms.openlocfilehash: 53ca4005f5681cfc5d550301d8aad1406aceb3a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717197"
---
# <a name="addfile-method"></a>AddFile 方法

將檔案加入至元件。 也可以用來建立未系結的模組。  
  
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
 要擴充之元件的唯一識別碼。  
  
 `pszFilename`  
 要加入之檔案的完整名稱。  
  
 `dwFlags`  
 COM + FileDef 旗標 `ffContainsNoMetaData` ，例如和 `ffWriteable` 。 `dwFlags` 會傳遞至 [DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pEmitter`  
 要用來發出中繼資料的[IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面（如有必要）。  
  
 `pFileToken`  
 將儲存所新增檔案之唯一識別碼的位置指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
