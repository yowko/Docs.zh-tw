---
title: CreateCoreClrDebugTarget 函式
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179212"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget 函式
創建與在遠端電腦上運行的調試器代理的連接，並返回一個[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件，該物件可用於查詢遠端電腦上的正在運行的進程和載入的運行時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwAddress`  
 [in] 遠端目標電腦的 IPv4 位址。  
  
 `ppTarget`  
 [出]指向將創建的[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件的指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_OUTOFMEMORY  
 無法為 `ppTarget` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 核心Clr遠端偵錯介面.h  
  
 **資料庫：** mscordbi_macx86.dll  
  
 **.NET 框架版本：** 3.5 SP1
