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
ms.openlocfilehash: fa6297e926d53c02bb0d1af7b59b45b8ee152399
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616459"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 函式
`CoUninitializeEE`已過時，不提供任何功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>備註  
 無法從進程中卸載 common language runtime 執行引擎。 若要關閉執行引擎呼叫[CorExitProcess](corexitprocess-function.md)。  
  
## <a name="see-also"></a>另請參閱

- [CoInitializeEE 函式](coinitializeee-function.md)
- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
