---
title: ICorPublishEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421172"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum 介面
做為列舉值的抽象基底介面，這些列舉值是用來發行進程和應用程式域的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](icorpublishenum-clone-method.md)|建立這個 `ICorPublishEnum` 物件的複本。|  
|[GetCount 方法](icorpublishenum-getcount-method.md)|取得列舉中的專案數。|  
|[Reset 方法](icorpublishenum-reset-method.md)|將的資料指標移至列舉的開頭。|  
|[Skip 方法](icorpublishenum-skip-method.md)|在列舉中，將資料指標向後移動指定的專案數。|  
  
## <a name="remarks"></a>備註  
 下列枚舉器衍生自 `ICorPublishEnum` ：  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorpubPublish Coclass](corpubpublish-coclass.md)
- [偵錯介面](debugging-interfaces.md)
