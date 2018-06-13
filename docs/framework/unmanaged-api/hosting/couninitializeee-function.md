---
title: CoUninitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73fa281d28e9b5362ff386b55b07dd431f1915f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429178"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 函式
`CoUninitializeEE` 已經過時，不提供功能。  
  
## <a name="syntax"></a>語法  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>備註  
 Common language runtime 執行引擎無法從處理序卸載。 若要關閉執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CoInitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
