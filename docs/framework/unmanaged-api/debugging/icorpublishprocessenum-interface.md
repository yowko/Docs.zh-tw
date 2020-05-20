---
title: ICorPublishProcessEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421068"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum 介面
[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽[ICorPublishProcess](icorpublishprocess-interface.md)物件的集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[下一個方法](icorpublishprocessenum-next-method.md)|`ICorPublishProcess`從目前位置開始，取得集合中指定數目的實例。|  
  
## <a name="remarks"></a>備註  
 介面會實 `ICorPublishProcessEnum` [ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。  
  
 `ICorPublishProcessEnum`實例是由[ICorPublish：： EnumProcesses](icorpublish-enumprocesses-method.md)方法所建立。 物件集合的遍歷 `ICorPublishProcess` 是以建立實例時所指定的篩選準則為基礎 `ICorPublishProcessEnum` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
