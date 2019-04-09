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
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163016"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 函式
尋找並載入 DLL 的訊息。 如果訊息 DLL 無法找到或載入，則會傳回 0。 訊息 DLL 應該的子目錄，其名稱是語言識別碼、 中或在目前的目錄。  
  
## <a name="syntax"></a>語法  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** alink.h  
  
 **程式庫**: alink.dll  
  
## <a name="see-also"></a>另請參閱

- [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
