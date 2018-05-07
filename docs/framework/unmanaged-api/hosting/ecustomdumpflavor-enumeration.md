---
title: ECustomDumpFlavor 列舉
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d0ba3f722f63650a3db6a8f633189993db0716
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor 列舉
包含值，表示哪些項目来納入的自訂子堆積的傾印時報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|指定自訂堆積傾印應該開始為小型傾印，並包含指定的任何額外的資料[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)執行個體會傳遞至相同的方法。|  
|`DUMP_FLAVOR_NonHeapCLRState`|指定自訂堆積傾印應該收集未以動態方式配置的所有執行階段狀態資料。|  
  
## <a name="remarks"></a>備註  
 類型的參數`ECustomDumpFlavor`傳遞至[iclrerrorreportingmanager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ECustomDumpItemKind 列舉](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
