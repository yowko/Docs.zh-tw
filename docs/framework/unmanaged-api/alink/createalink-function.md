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
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446551"
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
  
|參數|描述|  
|---------------|-----------------|  
|`riid`|其中一個元件連結器介面的機構名稱。|  
|`ppInterface`|成功完成時的位置包含 `riid` 介面的指標。|  
  
## <a name="requirements"></a>需求  
 連結**庫**： alink .dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (組件連結器)](../../tools/al-exe-assembly-linker.md)
