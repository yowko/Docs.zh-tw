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
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441587"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 介面
擴充符號系結器介面。 `QueryInterface`在執行介面的物件上呼叫，以取得此介面 `ISymUnmanagedBinder` 。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderFromCallback 方法](isymunmanagedbinder3-getreaderfromcallback-method.md)|可讓使用者透過回呼來執行或提供， `IID_IDiaReadExeAtRVACallback` 或 `IID_IDiaReadExeAtOffsetCallback` 從記憶體取得 Debug 目錄資訊|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 介面](isymunmanagedbinder2-interface.md)
