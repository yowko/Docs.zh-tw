---
title: IEnumDefinitionIdentity 介面
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: f3872a2b03d3b22d695af1c104e9ae8ba8856990
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729001"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity 介面

作為物件集合的列舉值 `IDefinitionIdentity` 。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|取得新物件的介面指標 `IEnumDefinitionIdentity` ，該物件包含與這個相同的成員 `IEnumDefinitionIdentity` 。|  
|`IEnumDefinitionIdentity::Next`|`IDefinitionIdentity`從目前位置開始取得指定數目的物件。|  
|`IEnumDefinitionIdentity::Reset`|將指令指標移至這個的開頭 `IEnumDefinitionIdentity` 。|  
|`IEnumDefinitionIdentity::Skip`|從目前位置開始，將指令指標向下移動指定數目的元素。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IDefinitionIdentity 介面](idefinitionidentity-interface.md)
