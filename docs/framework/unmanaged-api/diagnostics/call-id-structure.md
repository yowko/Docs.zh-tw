---
title: CALL_ID 結構
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769506"
---
# <a name="callid-structure"></a>CALL_ID 結構
提供偵錯工具所呼叫之函數的相關資訊。 請參閱[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)介面，如需詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`szMachine`|識別正在進行呼叫的電腦。|  
|`dwPid`|識別電腦處理器。|  
|`pUserThread`|識別正在執行呼叫的執行緒。|  
|`addrStackPointer`|指定的呼叫堆疊的位址。|  
|`szEntryPoint`|指定呼叫的位址。|  
|`szDestinationMachine`|識別將會執行呼叫的電腦。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱

- [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
