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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787472"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 函式
尋找並載入訊息 DLL。 如果無法找到或載入訊息 DLL，則傳回0。 訊息 DLL 應位於名稱為語言識別項的子目錄中，或在目前的目錄中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** alink。h  
  
 連結**庫**： alink .dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (組件連結器)](../../tools/al-exe-assembly-linker.md)
