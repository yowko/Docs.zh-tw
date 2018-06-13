---
title: ISymUnmanagedENCUpdate 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05cbe098b73dd817546dd72f0fc98ad548f75386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425414"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate 介面
[編輯後繼續] 功能提供函式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetLocalVariableCount 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|取得區域變數的數目。|  
|[GetLocalVariables 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|取得區域變數。|  
|[InitializeForEnc 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|可讓方法的第一個呼叫之前要計算的界限[isymunmanagedencupdate:: Updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)方法。|  
|[UpdateMethodLines 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。 允許每個陳述式的差異。|  
|[UpdateSymbolStore2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|讓編譯器將省略程式資料庫 (PDB) 資料流，從尚未經過修改的函式，前提是行資訊符合的需求。 使用舊的 PDB 行資訊和函式中的所有行的一個差異，您可以判斷正確的行資訊。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
