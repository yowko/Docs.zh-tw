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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6f514cc070a0a38eb09a5387efc8611100765b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944101"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 介面
擴充符號系結器介面。 在執行`ISymUnmanagedBinder`介面的物件`QueryInterface`上呼叫, 以取得此介面。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫 (PDB) 檔案會有安全性風險。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReaderFromCallback 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|可讓使用者透過回呼`IID_IDiaReadExeAtRVACallback`來執行或提供, 或`IID_IDiaReadExeAtOffsetCallback`從記憶體取得 Debug 目錄資訊|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl, CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
