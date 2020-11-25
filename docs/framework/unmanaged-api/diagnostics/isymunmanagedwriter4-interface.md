---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725803"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 介面

ISymUnmanagedWriter4 介面。  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>方法  

 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDebugInfoWithPadding 方法](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|函式與 [GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md) 相同，不同之處在于路徑字串在結束的 null 字元之後會以零填補，以使字串資料成為固定的大小 `MAX_PATH` 。 只有當路徑字串長度本身小於時，才會提供填補 `MAX_PATH` 。<br /><br /> 這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)
