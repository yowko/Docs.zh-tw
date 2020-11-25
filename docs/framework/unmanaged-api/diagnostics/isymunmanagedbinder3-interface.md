---
title: ISymUnmanagedBinder3 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 0cb0b91f2dca8203c37599400b3b61f84eb7d282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727311"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 介面

擴充符號系結器介面。 藉由 `QueryInterface` 在執行介面的物件上呼叫來取得這個介面 `ISymUnmanagedBinder` 。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫 (PDB) 檔案，會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderFromCallback 方法](isymunmanagedbinder3-getreaderfromcallback-method.md)|允許使用者透過回呼或 `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` 從記憶體中取得 Debug 目錄資訊來執行或提供|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)
