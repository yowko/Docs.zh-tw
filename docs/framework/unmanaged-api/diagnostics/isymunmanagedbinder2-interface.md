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
ms.openlocfilehash: c5a43f6c277f582f9f14cefe5bfba6f5300c09d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727350"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 介面

代表非受控碼的符號系結器，並擴充 [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) 介面。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫 (PDB) 檔案，會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile2 方法](isymunmanagedbinder2-getreaderforfile2-method.md)|指定中繼資料介面和檔案名之後，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面，以讀取與模組相關聯的偵錯工具符號。 提供比 [ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) 方法更廣泛的搜尋。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 介面](isymunmanagedbinder3-interface.md)
