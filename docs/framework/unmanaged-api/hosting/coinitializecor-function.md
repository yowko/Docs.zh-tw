---
title: CoInitializeCor 函式
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 1263467fc5db92d4dd21c4f09a98af309e2c4d55
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504416"
---
# <a name="coinitializecor-function"></a>CoInitializeCor 函式
`CoInitializeCor` 已經過時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a>備註  
 若要初始化 common language runtime，請使用[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。  
  
## <a name="requirements"></a>規格需求  
 **標頭：** Cor。h  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
