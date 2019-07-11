---
title: CertFreeAuthenticodeSignerInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42f5685a9a976be7a3a73badf286f77216e43106
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741239"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo 函式
釋出配置給資源[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>參數  
 `pSignerInfo`  
 [in, out] 所要發行的簽署人資訊。 請參閱[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
