---
title: SetNonAssemblyFlags 方法
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27ad89f1910bc7bb08a23c9fdb0d50828fb8b5e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741445"
---
# <a name="setnonassemblyflags-method"></a>SetNonAssemblyFlags 方法
設定不是組件特定的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `afFlags`  
 ALink 旗標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
