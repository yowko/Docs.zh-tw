---
title: ICLRStrongName2 介面
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092237"
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 介面
提供使用 SHA-2 安全雜湊演算法（SHA-256、SHA-384 和 SHA-512）群組建立強式名稱的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx 方法](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。|  
|[StrongNameSignatureVerificationEx2 方法](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
