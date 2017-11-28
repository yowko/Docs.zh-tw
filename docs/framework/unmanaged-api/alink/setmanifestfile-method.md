---
title: "SetManifestFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a>SetManifestFile 方法
可讓您指定或重設連結器會使用時，它會建立組件資訊清單檔案。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `pszFile`  
  
 其內容會放入 Win32 資源 blob 資訊清單檔案的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 Win32ResBlob 要求之前呼叫這個方法。 值`pszFile`參數就是其內容會讀取並放入 RT_MANIFEST 的識別碼使用的 Win32 資源資訊清單檔案的名稱。 當使用 NULL 參數呼叫，會清除任何先前讀取資訊清單。 這可讓連結器的狀態重設為初始設定時。  
  
## <a name="requirements"></a>需求  
 需要 aLink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink3 介面](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
