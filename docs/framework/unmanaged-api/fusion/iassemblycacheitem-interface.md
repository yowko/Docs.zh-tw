---
title: IAssemblyCacheItem 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796715"
---
# <a name="iassemblycacheitem-interface"></a>IAssemblyCacheItem 介面
代表全域組件快取中的單一元件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AbortItem 方法](iassemblycacheitem-abortitem-method.md)|允許全域組件快取中的元件在釋放之前執行清除作業。|  
|[Commit 方法](iassemblycacheitem-commit-method.md)|認可記憶體的快取元件參考。|  
|[CreateStream 方法](iassemblycacheitem-createstream-method.md)|建立具有指定之名稱和格式的資料流程。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [全域組件快取](../../app-domains/gac.md)
- [IAssemblyCache 介面](iassemblycache-interface.md)
