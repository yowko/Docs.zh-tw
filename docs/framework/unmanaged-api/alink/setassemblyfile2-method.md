---
title: SetAssemblyFile2 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 131f5d951e524ef48f2cfe1e3e88ef80ac21c452
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703677"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 方法

設定新元件的和選項的名稱。 當您產生未系結的模組時，請勿呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `pszFilename`  
 資訊清單檔的名稱。  
  
 `pEmitter`  
 這個檔案的[IMetaDataEmit2 介面](../metadata/imetadataemit2-interface.md)介面。  
  
 `afFlags`  
 [AssemblyFlags 列舉](../metadata/assemblyflags-enumeration.md)所代表的選項。  
  
 `pAssemblyID`  
 接收所要建立之元件的唯一識別碼。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
