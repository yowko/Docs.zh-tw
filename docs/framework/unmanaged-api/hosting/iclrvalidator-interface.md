---
title: ICLRValidator 介面
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762028"
---
# <a name="iclrvalidator-interface"></a>ICLRValidator 介面
提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FormatEventInfo 方法](iclrvalidator-formateventinfo-method.md)|取得有關指定之驗證錯誤的詳細訊息。|  
|[Validate 方法](iclrvalidator-validate-method.md)|驗證指定檔案中的可攜式可執行檔或 Microsoft 中繼語言（MSIL）。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl，IValidator。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRErrorReportingManager 介面](iclrerrorreportingmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
- [CLRRuntimeHost Coclass](clrruntimehost-coclass.md)
