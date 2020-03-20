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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179406"
---
# <a name="exportnestedtype-method"></a>ExportNestedType 方法
將巢狀型別指定為可匯出類型。 [匯出類型方法](exporttype-method.md)還可以匯出巢狀型別，但此方法更快。  
  
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
 要匯出的程式集的 ID。  
  
 `FileToken`  
 檔權杖或檔程式集，用於定義要匯出的類型。  
  
 `TypeToken`  
 類型權杖，使可匯出。  
  
 `ParentType`  
 父類型的權杖。  
  
 `pszTypename`  
 要匯出的完全限定類型名稱。  
  
 `dwFlags`  
 `ComType`標誌，如`tdPublic``tdNested`或 。 此值可以傳遞給[定義匯出類型方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。  
  
 `pType`  
 接收匯出類型的權杖。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則返回S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
