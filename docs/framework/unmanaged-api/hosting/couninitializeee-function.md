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
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136856"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 函式
`CoUninitializeEE` 已過時，而且沒有提供任何功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>備註  
 無法從進程中卸載 common language runtime 執行引擎。 若要關閉執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。  
  
## <a name="see-also"></a>請參閱

- [CoInitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
