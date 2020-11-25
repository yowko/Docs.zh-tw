---
title: IValidator 介面
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: ce417402231d03828243bfb8bb7543c0a644a882
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700986"
---
# <a name="ivalidator-interface"></a>IValidator 介面

提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|Validate|驗證指定的 PE 或 Microsoft 中繼語言 (MSIL) 檔。|  
|FormatEventInfo|取得對應到指定之驗證錯誤的錯誤訊息。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl、IValidator。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
