---
title: "GetALinkMessageDll 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16657c62d66db1570ad379ff5d42a75aaf3ea2a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
