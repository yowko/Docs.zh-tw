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
ms.openlocfilehash: cf73ada36be66edb3fa267d61873ae9acb088a34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717041"
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
 要匯入之檔案的唯一識別碼，取自 [ImportFile 方法](importfile-method.md)。  
  
 `dwFlags`  
 COM + FileDef 旗標 `ffContainsNoMetaData` ，例如和 `ffWriteable` 。 `dwFlags` 會傳遞至 [DefineFile 方法](../metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pFileToken`  
 接收所產生檔案之識別碼的權杖指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
