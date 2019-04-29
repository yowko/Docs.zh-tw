---
title: ISymUnmanagedBinder 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940058"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder 介面
表示 unmanaged 程式碼的符號繫結器。  
  
> [!IMPORTANT]
>  它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的結構。|  
|[GetReaderFromStream 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|提供中繼資料介面並包含符號存放區的資料流，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)指定的符號存放區的結構，將讀取偵錯符號。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [ISymUnmanagedBinder3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
