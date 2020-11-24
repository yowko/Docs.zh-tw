---
title: GetALinkMessageDll 函式
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684742"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 函式

尋找並載入訊息 DLL。 如果無法找到或載入訊息 DLL，則傳回0。 訊息 DLL 應該在名稱為語言識別項或目前目錄中的子目錄中。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>需求  

 **標頭：** alink。h  
  
 連結 **庫**： alink.dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (元件連結器) ](../../tools/al-exe-assembly-linker.md)
