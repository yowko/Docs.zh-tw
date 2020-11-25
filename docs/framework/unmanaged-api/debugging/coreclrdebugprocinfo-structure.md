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
ms.openlocfilehash: 5996393fd1a0504f9c3d3f9f07aa0e3d886a0787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719693"
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`m_dwPID`|作業系統指派的處理序識別碼。|  
|`m_dwInternalID`|在目標電腦上執行之遠端偵錯 Proxy 所指派的處理序識別碼。 這個識別碼回收的頻率比作業系統識別碼少。|  
|`m_wszName`|處理序的命令列。 這個成員可能會被截斷。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結 **庫：** mscordbi_macx86.dll  
  
 **.NET Framework 版本：** 3.5 SP1
