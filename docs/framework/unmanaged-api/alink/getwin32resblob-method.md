---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c77ade46d2401e2499a94504808efd94f79f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789788"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob 方法
擷取 Win32 資源的 blob。 設定組件選項之後呼叫這個方法。  
  
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
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 組件的識別碼。  
  
 `FileToken`  
 用來擷取建構的 Win32 版本資源時所要使用的檔名語彙基元檔案  
  
 `fDll`  
 如果檔案是 DLL，false EXE，則為 TRUE。  
  
 `pszIconFile`  
 若要將資源的 blob 插入的選擇性圖示。  
  
 `ppResBlob`  
 收到資源的 blob。  
  
 `pcbResBlob`  
 接收 blob 的大小。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
