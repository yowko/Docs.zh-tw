---
title: SetPEKind 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787187"
---
# <a name="setpekind-method"></a>SetPEKind 方法
決定可移植的可執行檔案類型，可能是電腦特定或電腦中立。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 元件的識別碼。  
  
 `FileToken`  
 要設定 PE 類型的檔案標記。 如果未指出未`AssemblyID`系結的 .netmodule，則可以是 Null。  
  
 `dwPEKind`  
 PE 的類型，如[CorPEKind 列舉](../metadata/corpekind-enumeration.md)所表示。  
  
 `dwMachine`  
 如 NT 標頭所示的目的電腦架構。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [GetPEKind 方法](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
