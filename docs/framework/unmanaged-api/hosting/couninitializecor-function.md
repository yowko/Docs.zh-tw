---
title: CoUninitializeCor 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3ce0b9a40d5375f563662d73964d28724209dcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758302"
---
# <a name="couninitializecor-function"></a>CoUninitializeCor 函式
`CoUninitializeCor` 已經過時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a>備註  
 Common language runtime 無法從處理序卸載。 若要完全移除執行中處理序的執行階段，您必須關閉該程序。  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
