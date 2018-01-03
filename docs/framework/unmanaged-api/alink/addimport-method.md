---
title: AddImport Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
 COM + FileDef 旗標，例如`ffContainsNoMetaData`和`ffWriteable`。 `dwFlags`傳遞至[DefineFile 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。  
  
 `pFileToken`  
 接收所產生的檔案 ID 的語彙基元指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
