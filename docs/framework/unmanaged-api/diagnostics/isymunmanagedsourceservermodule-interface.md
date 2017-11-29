---
title: "ISymUnmanagedSourceServerModule 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule
helpviewer_keywords: ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3110be6a42ce68a6a8b3571206244a7fd1d38b8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsourceservermodule-interface"></a>ISymUnmanagedSourceServerModule 介面
提供模組中的來源伺服器資料。 取得此介面，藉由呼叫`QueryInterface`實作的物件上[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[GetSourceServerData 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|傳回模組的來源伺服器資料。|  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
