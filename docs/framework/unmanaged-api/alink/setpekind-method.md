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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179380"
---
# <a name="setpekind-method"></a>SetPEKind 方法
確定可移植可執行類型，無論是特定于機器還是與機器無關。  
  
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
 程式集的 ID。  
  
 `FileToken`  
 要為其設置 PE 類型的檔權杖。 如果未`AssemblyID`指示未綁定網路模組，則可以為 Null。  
  
 `dwPEKind`  
 PE 的類型，如[CorPEKind 枚舉](../metadata/corpekind-enumeration.md)所示。  
  
 `dwMachine`  
 目的電腦體系結構，如 NT 標頭中所示。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則返回S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h.  
  
## <a name="see-also"></a>另請參閱

- [GetPEKind 方法](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
