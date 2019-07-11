---
title: CoUninitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
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
ms.openlocfilehash: d05bc472711838236ed18b00ce808d022d9581dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758209"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 函式
`CoUninitializeEE` 已經過時，不提供功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>備註  
 Common language runtime 執行引擎無法從處理序卸載。 若要關閉的執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。  
  
## <a name="see-also"></a>另請參閱

- [CoInitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
