---
title: AddImport Method1
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
ms.openlocfilehash: 98fefc0240f6496a3e7bfb491e27a57e98cfea1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="addimport-method1"></a>AddImport Method1
將組件匯入。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 要當做引數的組件的唯一識別碼。  
  
 `ImportToken`  
 唯一識別碼，從擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，要匯入檔案。  
  
 `dwFlags`  
 COM + FileDef 旗標，例如`ffContainsNoMetaData`和`ffWriteable`。 `dwFlags` 傳遞至[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pFileToken`  
 接收所產生的檔案 ID 的語彙基元指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
