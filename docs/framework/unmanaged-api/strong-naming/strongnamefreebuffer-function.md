---
title: StrongNameFreeBuffer 函式
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: d93bda046a79dbdec2195eee48fefc1e5538b2e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732251"
---
# <a name="strongnamefreebuffer-function"></a>StrongNameFreeBuffer 函式

釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbMemory`  
 在要釋放之記憶體的指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameFreeBuffer 方法](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
