---
title: ExportNestedType 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0afe4daa1c85f3e15addac55bdbe631d40e03f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407560"
---
# <a name="exportnestedtype-method"></a>ExportNestedType 方法
指定巢狀型別為可匯出。 [ExportType 方法](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md)也可以匯出巢狀類型，但這個方法會比較快。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 若要從匯出的組件識別碼。  
  
 `FileToken`  
 檔案的語彙基元或組件的檔案，它定義成可匯出的類型。  
  
 `TypeToken`  
 輸入成可匯出類型的語彙基元。  
  
 `ParentType`  
 父類型的語彙基元。  
  
 `pszTypename`  
 若要匯出的完整限定的類型名稱。  
  
 `dwFlags`  
 `ComType` 旗標，例如`tdPublic`或`tdNested`。 此值可能會傳遞至[DefineExportedType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)。  
  
 `pType`  
 接收匯出類型的語彙的基元。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
