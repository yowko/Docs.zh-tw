---
title: ExportNestedTypeForwarder 方法
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb8112d6d2b5c2cbb257db2f20ff4be5a84e827b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787460"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder 方法
將巢狀型別的類型轉寄站加入至指定元件的類型資料表。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
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
 定義類型之檔案的檔案標記或元件識別碼。  
  
 `TypeToken`  
 類型的 Token。  
  
 `ParentType`  
 父類型的 Token。  
  
 `pszTypename`  
 要匯出的完整類型名稱。  
  
 `dwFlags`  
 `ComType`旗標， `tdPublic`例如`tdNested`或。  
  
 `pType`  
 接收匯出類型的 token。 這只有在發出巢狀型別時才需要。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
