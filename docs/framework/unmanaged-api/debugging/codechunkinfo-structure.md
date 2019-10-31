---
title: CodeChunkInfo 結構
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132392"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo 結構

代表記憶體中的單一程式碼區塊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`startAddr`|`CORDB_ADDRESS` 值，指定區塊的起始位址。|  
|`length`|區塊的大小（以位元組為單位）。|  
  
## <a name="remarks"></a>備註  
 程式碼的單一區塊是機器碼的區域，而機器碼是程式碼物件的一部分，例如函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetCodeChunks 方法](icordebugcode2-getcodechunks-method.md)
- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
