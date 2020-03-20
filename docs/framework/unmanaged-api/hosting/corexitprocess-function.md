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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176457"
---
# <a name="corexitprocess-function"></a>CorExitProcess 函式
關閉當前非託管進程。  
  
 此功能已在 .NET 框架 4 中棄用。 改用[ICLRMetaHost：：退出進程](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法。  
  
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
> 從 .NET 框架 4`CorExitProcess`開始，退出進程中的每個啟動運行時，而不僅僅是將舊 API 綁定到的運行時。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
