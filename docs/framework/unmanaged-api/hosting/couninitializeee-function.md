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
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687843"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 函式

`CoUninitializeEE` 已淘汰，不提供任何功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>備註  

 Common language runtime 執行引擎無法從進程中卸載。 若要關閉執行引擎呼叫 [CorExitProcess](corexitprocess-function.md)。  
  
## <a name="see-also"></a>另請參閱

- [CoInitializeEE 函式](coinitializeee-function.md)
- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
