---
title: EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: 6a5b3f1e9bf1444feb73949ef7133fbd9ae35134
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446467"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes 方法
抓取元件層級的自訂屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `hEnum`  
 列舉值的控制碼。  
  
 `tkType`  
 要列舉的屬性類型。 針對所有屬性使用 `mdTokenNill`。  
  
 `rCustomValues`  
 接收自訂屬性標記。  
  
 `cMax`  
 指定 `rCustomValues` 陣列的大小。  
  
 `pcCustomValues`  
 選擇性地接收權杖值的計數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
