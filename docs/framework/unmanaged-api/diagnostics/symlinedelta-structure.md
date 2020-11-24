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
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690937"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 結構

提供有關方法的符號處理常式資訊，這些方法是在編輯時移動的。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`mdMethod`|方法的元資料標記。|  
|`delta`|移動方法的行數。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區結構](diagnostics-symbol-store-structures.md)
