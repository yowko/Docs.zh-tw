---
title: ICLRHostProtectionManager 介面
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: e8ead998907d55b0bfbf82e5f6f4e7c504f657ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714155"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager 介面

讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|保證永遠不會發生會導致嚴重的 common language runtime (CLR) 錯誤的特定罕見競爭情形。|  
|[SetProtectedCategories 方法](iclrhostprotectionmanager-setprotectedcategories-method.md)|指定應封鎖在部分信任程式碼中執行之 managed 類型和成員的類別。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EApiCategories 列舉](eapicategories-enumeration.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
