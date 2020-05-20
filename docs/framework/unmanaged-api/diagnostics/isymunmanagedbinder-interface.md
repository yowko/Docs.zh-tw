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
ms.openlocfilehash: f4f925282d65cd9cbc8eb1c8825f358602de68ed
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441691"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder 介面
表示非受控程式碼的符號系結器。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderForFile 方法](isymunmanagedbinder-getreaderforfile-method.md)|提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)結構，以讀取與模組相關聯的偵錯工具符號。|  
|[GetReaderFromStream 方法](isymunmanagedbinder-getreaderfromstream-method.md)|假設中繼資料介面和包含符號存放區的資料流程，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)結構，以便從指定的符號存放區讀取偵錯工具符號。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)
- [ISymUnmanagedBinder3 介面](isymunmanagedbinder3-interface.md)
