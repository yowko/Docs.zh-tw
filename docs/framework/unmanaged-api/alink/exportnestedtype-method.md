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
ms.openlocfilehash: fded6b95144d4088a2abc8dfcc4ef8eda331c34f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438430"
---
# <a name="exportnestedtype-method"></a>ExportNestedType 方法
將巢狀型別指定為可匯出。 [ExportType 方法](exporttype-method.md)也可以匯出巢狀型別，但是這個方法更快。  
  
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
 要匯出之元件的識別碼。  
  
 `FileToken`  
 檔案的檔案標記或檔案元件，定義要成為可匯出的類型。  
  
 `TypeToken`  
 要成為可匯出之類型的類型 token。  
  
 `ParentType`  
 父類型的 Token。  
  
 `pszTypename`  
 要匯出的完整類型名稱。  
  
 `dwFlags`  
 `ComType` 旗標，例如 `tdPublic` 或 `tdNested`。 這個值可能會傳遞給[DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。  
  
 `pType`  
 接收匯出類型的 token。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
