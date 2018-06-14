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
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402213"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 函式
尋找並載入 DLL 的訊息。 如果訊息 DLL 無法找到或載入，則傳回 0。 訊息 DLL 應該的子目錄，其名稱是語言識別碼、 中或在目前的目錄。  
  
## <a name="syntax"></a>語法  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** alink.h  
  
 **程式庫**: alink.dll  
  
## <a name="see-also"></a>另請參閱  
 [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
