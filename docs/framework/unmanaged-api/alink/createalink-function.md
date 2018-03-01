---
title: "CreateALink 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a>CreateALink 函式
建立組件連結器的執行個體，並設定指定之介面的指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`riid`|其中一個組件連結器介面的實體名稱。|  
|`ppInterface`|成功完成時包含位置的指標`riid`介面。|  
  
## <a name="requirements"></a>需求  
 **程式庫**: alink.dll  
  
## <a name="see-also"></a>請參閱  
 [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
