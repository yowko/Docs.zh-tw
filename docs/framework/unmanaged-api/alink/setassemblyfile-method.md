---
title: SetAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 45eed17b91f70d4188d1d89fc91a41455f3e845b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732641"
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile 方法

指派要建立之元件的名稱。 無法在產生未系結的模組時使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `pszFilename`  
 資訊清單檔案的完整名稱。  
  
 `pEmitter`  
 [IMetaDataEmit 介面](../metadata/imetadataemit-interface.md)介面的指標。  
  
 `afFlags`  
 [AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)中所定義的旗標。  
  
 `pAssemblyID`  
 所產生元件的識別碼指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
