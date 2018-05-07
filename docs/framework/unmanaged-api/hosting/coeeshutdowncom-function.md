---
title: CoEEShutDownCOM 函式
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0b30cc2c499644ffc97a734e1554e4e352b34af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 函式
強制執行 common language runtime (CLR) 版本保留在執行階段可呼叫包裝函式 (RCW) 內的所有介面指標。 這有釋放所有 RCW 快取的影響。 此全域函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 相反地，使用特定的執行階段的進入點。  
  
## <a name="syntax"></a>語法  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>備註  
 `CoEEShutDownCOM`函式第一次釋放和所有的快取中所有內容中的所有 Rcw，，然後移除任何現有的安裝程式中的終止程式通知。 沒有 DLL 卸載就會發生。  
  
> [!CAUTION]
>  此函式會影響所有的執行階段載入處理序。  
  
 開頭為[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]，對您要影響的特定執行階段的這個函式呼叫的進入點。 若要取得的進入點，請呼叫[iclrruntimeinfo:: Getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定"CoEEShutDownCOM"。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
