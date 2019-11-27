---
title: EmitAssemblyCustomAttribute 方法
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446515"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute 方法
呼叫以設定元件層級的自訂屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 元件的識別碼。  
  
 `FileToken`  
 定義屬性的檔案。 如果 `AssemblyID` 未指出未系結的 .netmodule，則可以是 Null。  
  
 `tkType`  
 自訂屬性的類型。  
  
 `pCustomValue`  
 自訂值資料。  
  
 `cbCustomValue`  
 自訂值資料的長度。  
  
 `bSecurity`  
 如果自訂屬性與元件簽署有關，則為 TRUE。  
  
 `bAllowMulti`  
 如果要發出多個屬性，則為 TRUE。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
