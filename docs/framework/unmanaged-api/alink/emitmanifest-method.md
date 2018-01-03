---
title: "EmitManifest 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11966eccfdbbdbab29d305915afd904a54f9c57b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="emitmanifest-method"></a>EmitManifest 方法
發出的最後一個資訊清單。 匯入所有其他檔案，並設定所有選項之後呼叫這個方法。 請勿呼叫這個方法未繫結的模組。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 組件的識別碼。  
  
 `pdwReserveSize`  
 要保留在組件檔案中，從擷取大小[StrongNameSignatureSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)。  
  
 `ptkManifest`  
 選擇性地接收組件資訊清單語彙基元。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
