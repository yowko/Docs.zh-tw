---
title: ICeeGen::GetIMapTokenIface 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIMapTokenIface
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIMapTokenIface
helpviewer_keywords:
- GetIMapTokenIface method [.NET Framework metadata]
- ICeeGen::GetIMapTokenIface method [.NET Framework metadata]
ms.assetid: 847a5531-c37d-49cd-8844-9e54b5d86cf7
topic_type:
- apiref
ms.openlocfilehash: 079a599ff87146c4eed4b15d57696338fb25f530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674303"
---
# <a name="iceegengetimaptokeniface-method"></a>ICeeGen::GetIMapTokenIface 方法

取得指定之標記所參考的介面。  
  
 這個方法已經過時，不應該使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetIMapTokenIface (  
    [in, out] IUnknown   **pIMapToken  
);  
```  
  
## <a name="parameters"></a>參數  

 `pIMapToken`  
 [in，out]要傳回之介面的元資料標記。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICeeGen 介面](iceegen-interface.md)
