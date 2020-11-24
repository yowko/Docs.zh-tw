---
title: CertFreeAuthenticodeTimestamperInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
ms.openlocfilehash: 1ef71b14faf66c179030dff2a7d953e27463c1f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674160"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a>CertFreeAuthenticodeTimestamperInfo 函式

釋出配置給 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) 結構的資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>參數  

 `pTimestamperInfo`  
 [in, out] 所要發行的時間戳記程式資訊。 請參閱 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) 結構。  
  
## <a name="return-value"></a>傳回值  

 如果函式成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](index.md)
