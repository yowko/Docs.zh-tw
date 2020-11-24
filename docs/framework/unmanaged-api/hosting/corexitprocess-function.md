---
title: CorExitProcess 函式
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: f6d8114732a3b7c15d0a0258a28a362d661b030a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673619"
---
# <a name="corexitprocess-function"></a>CorExitProcess 函式

關閉目前未受管理的進程。  
  
 此函式已在 .NET Framework 4 中被取代。 請改用 [ICLRMetaHost：： ExitProcess](iclrmetahost-exitprocess-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>參數  

 `exitCode`  
 指定進程結束代碼的整數。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 從 .NET Framework 4 開始， `CorExitProcess` 會在處理常式中結束每個啟動的執行時間，而不只是舊版 api 所系結的執行時間。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
