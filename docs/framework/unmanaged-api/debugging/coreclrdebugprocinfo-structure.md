---
title: CoreClrDebugProcInfo 結構
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132155"
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo 結構
代表正在遠端電腦上執行的處理序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`m_dwPID`|作業系統指派的處理序識別碼。|  
|`m_dwInternalID`|在目標電腦上執行之遠端偵錯 Proxy 所指派的處理序識別碼。 這個識別碼回收的頻率比作業系統識別碼少。|  
|`m_wszName`|處理序的命令列。 這個成員可能會被截斷。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結**庫：** mscordbi_macx86  
  
 **.NET Framework 版本：** 3.5 SP1
