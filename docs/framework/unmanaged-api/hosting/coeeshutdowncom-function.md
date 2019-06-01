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
- mscorsvr.dll
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
ms.openlocfilehash: 6a28b9d6e41d0572d423576f5b4024a60a70216c
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456860"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 函式
強制 common language runtime (CLR) 版本所有的介面指標，它就會保存於執行階段可呼叫包裝函式 (RCW)。 這有釋放 RCW 的所有快取的效果。 此全域函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 相反地，針對特定執行階段使用的進入點。  
  
## <a name="syntax"></a>語法  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>備註  
 `CoEEShutDownCOM`函式第一次釋放所有的快取，和所有的內容中的所有 Rcw，則會移除任何現有的安裝程式中的終止通知。 沒有 DLL 卸載時發生。  
  
> [!CAUTION]
>  此函式會影響所有的執行階段載入處理序。  
  
 從.NET Framework 4 開始，在您想要影響的特定執行階段上的這個函式呼叫的進入點。 若要取得的進入點，請呼叫[iclrruntimeinfo:: Getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定"CoEEShutDownCOM 」。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
