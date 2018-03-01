---
title: "ISymUnmanagedDocument 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument 介面
代表符號存放區所參考的文件。 文件是由統一資源定位器 (URL) 和 GUID 文件類型定義。 您可以找出不論如何使用 URL 儲存文件及文件類型的 GUID。 您可以在符號存放區中儲存的文件來源，並透過此介面擷取它。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindClosestLine 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|傳回最接近的一行，也就是序列點，在本文件也可能不是序列點中。|  
|[GetCheckSum 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|取得總和檢查碼。|  
|[GetCheckSumAlgorithmId 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼傳回全部為零的 GUID。|  
|[GetDocumentType 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|取得這份文件的文件類型。|  
|[GetLanguage 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|取得這份文件的語言識別項。|  
|[GetLanguageVendor 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|取得這份文件的語言廠商。|  
|[GetSourceLength 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|取得內嵌來源的長度 (以位元組為單位)。|  
|[GetSourceRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|傳回指定的範圍的內嵌的來源到指定的緩衝區。|  
|[GetURL 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|傳回這份文件的 URL。|  
|[HasEmbeddedSource 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|傳回`true`如果文件來源內嵌在偵錯符號; 否則傳回`false`。|  
  
## <a name="see-also"></a>請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
