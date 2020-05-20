---
title: SYMLINEDELTA 結構
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609296"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 結構
提供相關資訊給符號處理常式，而這些方法是因編輯結果而移動。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`mdMethod`|方法的元資料標記。|  
|`delta`|方法已移動的行數。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區結構](diagnostics-symbol-store-structures.md)
