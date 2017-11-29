---
title: "FExecuteInAppDomainCallback 函式指標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FExecuteInAppDomainCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FExecuteInAppDomainCallback
helpviewer_keywords: FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e6c04a964b50357dc3687f3faf5710505bae364
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a>FExecuteInAppDomainCallback 函式指標
指向由通用語言執行平台 (CLR) 執行 managed 程式碼呼叫的函式。  
  
 此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cookie`  
 [in]其中包含要執行的 managed 程式碼不透明呼叫端配置的記憶體指標。  
  
 配置和存留期這個記憶體是由呼叫端 (也就是 CLR) 控制。 這不是 CLR managed 堆積的記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorWks.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
