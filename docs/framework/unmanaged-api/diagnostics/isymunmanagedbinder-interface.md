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
ms.openlocfilehash: 554e59484f00626726f7f024c69e93a5e6647130
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727376"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder 介面

代表非受控碼的符號繫結器。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫 (PDB) 檔案，會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile 方法](isymunmanagedbinder-getreaderforfile-method.md)|指定中繼資料介面和檔案名之後，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 結構，以讀取與模組相關聯的偵錯工具符號。|  
|[GetReaderFromStream 方法](isymunmanagedbinder-getreaderfromstream-method.md)|指定中繼資料介面和包含符號存放區的資料流程時，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 結構，以便從指定的符號存放區讀取偵錯工具符號。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)
- [ISymUnmanagedBinder3 介面](isymunmanagedbinder3-interface.md)
