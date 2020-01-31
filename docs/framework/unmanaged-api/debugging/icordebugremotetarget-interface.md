---
title: ICorDebugRemoteTarget 介面
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: bab6b7f683b5563cf362366dfb007f83caeee12d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791928"
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget 介面
提供可讓開發人員對通用語言執行平台 (CLR) 環境中的 Silverlight 應用程式進行偵錯的方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName 方法](icordebugremotetarget-gethostname-method.md)|傳回遠端電腦的主機名稱或 IP 位址。|  
  
## <a name="remarks"></a>備註  
 Windows 95、Windows 98、Windows ME 或非 x86 的平台 (例如 IA-64 和 AMD64) 不支援混合模式 (也就是 Managed 和機器碼) 偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **Library：** ： corguids.lib. lib  
  
 **.NET Framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRemote 介面](icordebugremote-interface.md)
- [ICorDebug 介面](icordebug-interface.md)
- [偵錯介面](debugging-interfaces.md)
