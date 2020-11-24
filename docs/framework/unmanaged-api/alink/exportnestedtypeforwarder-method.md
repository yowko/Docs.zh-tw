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
ms.openlocfilehash: 45adda6551e1cec994f59acbb0e8d2b5c56c4df6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684807"
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
 定義類型之檔案的檔案 token 或元件識別碼。  
  
 `TypeToken`  
 類型的標記。  
  
 `ParentType`  
 父類型的標記。  
  
 `pszTypename`  
 要匯出的完整型別名稱。  
  
 `dwFlags`  
 `ComType` 旗標，例如 `tdPublic` 或 `tdNested` 。  
  
 `pType`  
 接收匯出類型的標記。 只有發出巢狀型別時，才需要這麼做。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
