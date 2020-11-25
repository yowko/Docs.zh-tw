---
title: AddFile2 方法
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717080"
---
# <a name="addfile2-method"></a>AddFile2 方法

將檔案加入至元件。 也可以用來建立未系結的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 要加入檔案的元件識別碼。  
  
 `pszFilename`  
 要加入的檔案名。  
  
 `dwFlags`  
 COM + `FileDef` 旗標 `ffContainsNoMetaData` ，例如和 `ffWriteable` 。 `dwFlags` 會傳遞至 [DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pEmitter`  
 介面 [IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md) 介面。  
  
 `pFileToken`  
 接收要加入之檔案的識別碼。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
