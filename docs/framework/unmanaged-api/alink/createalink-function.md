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
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683727"
---
# <a name="createalink-function"></a>CreateALink 函式

建立元件連結器的實例，並將指標設定為指定的介面。  
  
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
|`ppInterface`|成功完成時的位置會包含介面的指標 `riid` 。|  
  
## <a name="requirements"></a>需求  

 連結 **庫**： alink.dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (元件連結器) ](../../tools/al-exe-assembly-linker.md)
