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
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404092"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder 方法
將指定的組件的型別資料表中的巢狀類型的類型轉送子。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 若要從匯出的組件識別碼。  
  
 `FileToken`  
 語彙基元或組件的檔案識別碼定義類型的檔案。  
  
 `TypeToken`  
 類型的語彙基元。  
  
 `ParentType`  
 父類型的語彙基元。  
  
 `pszTypename`  
 若要匯出的完整限定的類型名稱。  
  
 `dwFlags`  
 `ComType` 旗標，例如`tdPublic`或`tdNested`。  
  
 `pType`  
 接收匯出類型的語彙的基元。 這是才需要發出巢狀型別。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
