---
title: "GetWin32ResBlob 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4456757c56440463010d4adc3d3eed90dbc07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob 方法
擷取 Win32 資源 blob。 設定組件選項之後呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 組件的識別碼。  
  
 `FileToken`  
 用來擷取建構的 Win32 版本資源時所要使用的檔名語彙基元檔案  
  
 `fDll`  
 如果檔案是 DLL，false EXE，則為 TRUE。  
  
 `pszIconFile`  
 要插入資源 blob 的選擇性圖示。  
  
 `ppResBlob`  
 接收資源 blob。  
  
 `pcbResBlob`  
 接收 blob 的大小。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
