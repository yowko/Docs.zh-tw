---
title: IMetaDataEmit::SetParent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: cef817b52718acfbc4360e9d3742a5a78abd3afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675044"
---
# <a name="imetadataemitsetparent-method"></a>IMetaDataEmit::SetParent 方法

建立指定的成員（如先前呼叫 [IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md)所定義）是所指定類型的成員，如先前呼叫 [IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md)所定義。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a>參數  

 `mr`  
 在 `mdMemberRef` 要接收新父系的權杖。  
  
 `tk`  
 在 `mdToken` 新父系的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
