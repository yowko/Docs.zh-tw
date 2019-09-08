---
title: AddImport 方法
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787659"
---
# <a name="addimport-method"></a>AddImport 方法
將匯入新增至元件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 要擴充之元件的唯一識別碼。  
  
 `ImportToken`  
 要匯入之檔案的唯一識別碼，從[ImportFile 方法](importfile-method.md)中取出。  
  
 `dwFlags`  
 Com + FileDef 旗標`ffContainsNoMetaData` ， `ffWriteable`例如和。 `dwFlags`會傳遞至[DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pFileToken`  
 Token 的指標，該權杖會接收所產生檔案的識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
