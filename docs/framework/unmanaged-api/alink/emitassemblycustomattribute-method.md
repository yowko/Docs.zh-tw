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
ms.openlocfilehash: 2070d1ec2aec80638c20c764eed5086c4a42e0fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676357"
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
 定義屬性的檔案。 如果未指出未系結 `AssemblyID` 的 .netmodule，則可以是 Null。  
  
 `tkType`  
 自訂屬性的類型。  
  
 `pCustomValue`  
 自訂值資料。  
  
 `cbCustomValue`  
 自訂值資料的長度。  
  
 `bSecurity`  
 如果自訂屬性與元件簽署相關，則為 TRUE。  
  
 `bAllowMulti`  
 如果要發出多個屬性，則為 TRUE。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
