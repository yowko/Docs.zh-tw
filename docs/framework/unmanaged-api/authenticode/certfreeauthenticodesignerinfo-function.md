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
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674173"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo 函式

釋出配置給 [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) 結構的資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>參數  

 `pSignerInfo`  
 [in, out] 所要發行的簽署人資訊。 請參閱 [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) 結構。  
  
## <a name="return-value"></a>傳回值  

 如果函式成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](index.md)
