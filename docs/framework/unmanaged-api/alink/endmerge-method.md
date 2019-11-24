---
title: EndMerge 方法
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: cacf7eab1e53f590ad46fd98ed2f5dcbd14cd30a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434415"
---
# <a name="endmerge-method"></a>EndMerge 方法
Indicates that all custom attributes have been merged into the emit scope.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 ID of the assembly.  
  
## <a name="return-value"></a>傳回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>需求  
 Requires alink.h  
  
## <a name="see-also"></a>請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
