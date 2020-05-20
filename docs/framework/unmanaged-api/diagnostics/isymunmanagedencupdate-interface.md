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
ms.openlocfilehash: aa4fe2185ead7edfa47d4194799c930193e04076
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614522"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate 介面
提供 [編輯後繼續] 功能的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetLocalVariableCount 方法](isymunmanagedencupdate-getlocalvariablecount-method.md)|取得本機變數的數目。|  
|[GetLocalVariables 方法](isymunmanagedencupdate-getlocalvariables-method.md)|取得本機變數。|  
|[InitializeForEnc 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|允許在第一次呼叫[ISymUnmanagedENCUpdate：： UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)方法之前計算方法界限。|  
|[UpdateMethodLines 方法](isymunmanagedencupdate-updatemethodlines-method.md)|允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。 允許每個語句的差異。|  
|[UpdateSymbolStore2 方法](isymunmanagedencupdate-updatesymbolstore2-method.md)|允許編譯器省略未從程式資料庫（PDB）資料流程修改的函式，但前提是行資訊符合需求。 您可以使用舊的 PDB 行資訊，以及函式中所有行的一個差異來判斷正確的行資訊。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
