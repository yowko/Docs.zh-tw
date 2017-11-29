---
title: "ICLRStrongName2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9e9a88f1064c888d60e363be569d06458299143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 介面
提供建立強式名稱使用 sha-2 群組 （sha-256、 sha-384 和 sha-512） 的安全雜湊演算法的能力。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx 方法](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|公開/私密金鑰組，從取得的公開金鑰，並指定雜湊演算法和簽章演算法。|  
|[StrongNameSignatureVerificationEx2 方法](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|驗證簽章是強式名稱組件，並提供從 ECMA 金鑰對應至實際的索引鍵。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
