---
title: ISymUnmanagedBinder2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9fbb8364fb967e739eb9807b26cbc65f0ebec1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944197"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 介面
表示非受控程式碼的符號系結器, 並擴充[ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)介面。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫 (PDB) 檔案會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|提供中繼資料介面和檔案名, 會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面, 以便讀取與模組相關聯的偵錯工具符號。 提供比[ISymUnmanagedBinder:: GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法更廣泛的搜尋。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl, CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
