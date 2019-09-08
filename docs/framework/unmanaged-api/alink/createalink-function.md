---
title: CreateALink 函式
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787625"
---
# <a name="createalink-function"></a>CreateALink 函式
建立元件連結器的實例，並設定指定介面的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`riid`|其中一個元件連結器介面的機構名稱。|  
|`ppInterface`|成功完成時的位置包含`riid`介面的指標。|  
  
## <a name="requirements"></a>需求  
 連結**庫**： alink .dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (組件連結器)](../../tools/al-exe-assembly-linker.md)
