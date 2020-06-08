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
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501829"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 介面
表示非受控程式碼的符號系結器，並擴充[ISymUnmanagedBinder](isymunmanagedbinder-interface.md)介面。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile2 方法](isymunmanagedbinder2-getreaderforfile2-method.md)|提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面，以便讀取與模組相關聯的偵錯工具符號。 提供比[ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)方法更廣泛的搜尋。|  
  
## <a name="requirements"></a>規格需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 介面](isymunmanagedbinder3-interface.md)
