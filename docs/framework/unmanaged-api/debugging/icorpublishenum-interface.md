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
ms.openlocfilehash: 492d4b727ce507340fec47d30a791aa49d0cecb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693342"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum 介面

作為列舉值的抽象基底介面，用於發行有關處理常式和應用程式域的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](icorpublishenum-clone-method.md)|建立這個 `ICorPublishEnum` 物件的複本。|  
|[GetCount 方法](icorpublishenum-getcount-method.md)|取得列舉中的專案數。|  
|[Reset 方法](icorpublishenum-reset-method.md)|將游標移至列舉的開頭。|  
|[Skip 方法](icorpublishenum-skip-method.md)|依指定的專案數將游標向前移動至列舉。|  
  
## <a name="remarks"></a>備註  

 下列列舉值衍生自 `ICorPublishEnum` ：  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorpubPublish Coclass](corpubpublish-coclass.md)
- [偵錯介面](debugging-interfaces.md)
