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
ms.openlocfilehash: 5e3c2ecd1bdd5c1181223c7500eb7473e20fa5d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731341"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate 介面

提供「編輯後繼續」功能的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetLocalVariableCount 方法](isymunmanagedencupdate-getlocalvariablecount-method.md)|取得本機變數的數目。|  
|[GetLocalVariables 方法](isymunmanagedencupdate-getlocalvariables-method.md)|取得區域變數。|  
|[InitializeForEnc 方法](isymunmanagedencupdate-initializeforenc-method.md)|允許在第一次呼叫 [ISymUnmanagedENCUpdate：： UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) 方法之前，先計算方法界限。|  
|[UpdateMethodLines 方法](isymunmanagedencupdate-updatemethodlines-method.md)|允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。 允許每個語句的差異。|  
|[UpdateSymbolStore2 方法](isymunmanagedencupdate-updatesymbolstore2-method.md)|允許編譯器省略尚未從程式資料庫修改的函式 (PDB) stream，前提是行資訊符合需求。 您可以使用舊的 PDB 行資訊，以及函式中所有行的一個差異來判斷正確的行資訊。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
