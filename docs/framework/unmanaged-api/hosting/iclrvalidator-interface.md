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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f34a9aac31fe50974a6f88416d0a00cd72aca8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511926"
---
# <a name="iclrvalidator-interface"></a>ICLRValidator 介面
提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FormatEventInfo 方法](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|取得有關指定之驗證錯誤的詳細的訊息。|  
|[Validate 方法](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|驗證的可攜式執行檔或 Microsoft intermediate language (MSIL)，在指定的檔案。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl, IValidator.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
