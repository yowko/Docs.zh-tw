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
ms.openlocfilehash: 69c99e2facfcb9077c3fc4131186ba3882c7cef6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684833"
---
# <a name="exportnestedtype-method"></a>ExportNestedType 方法

將巢狀型別指定為可匯出。 [ExportType 方法](exporttype-method.md)也可以匯出巢狀型別，但這個方法更快。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 要從中匯出之元件的識別碼。  
  
 `FileToken`  
 檔案的檔案 token 或元件，其定義要成為可匯出的型別。  
  
 `TypeToken`  
 要成為可匯出的型別權杖型別。  
  
 `ParentType`  
 父類型的標記。  
  
 `pszTypename`  
 要匯出的完整型別名稱。  
  
 `dwFlags`  
 `ComType` 旗標，例如 `tdPublic` 或 `tdNested` 。 這個值可以傳遞給 [DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。  
  
 `pType`  
 接收匯出類型的權杖。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
