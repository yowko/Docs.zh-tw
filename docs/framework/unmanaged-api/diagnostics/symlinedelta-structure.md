---
title: "SYMLINEDELTA 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: SYMLINEDELTA
api_location: diasymreader.dll
api_type: COM
f1_keywords: SYMLINEDELTA
helpviewer_keywords: SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd83560516e946c03a0ea71cf79fe6d3396bacb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 結構
提供符號處理常式已編輯移動的方法相關的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`mdMethod`|方法的中繼資料語彙基元。|  
|`delta`|方法已移動的行數。|  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
