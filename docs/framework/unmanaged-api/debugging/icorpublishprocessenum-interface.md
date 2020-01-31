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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790501"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum 介面
[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽[ICorPublishProcess](icorpublishprocess-interface.md)物件的集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icorpublishprocessenum-next-method.md)|從目前位置開始，取得集合中指定數目的 `ICorPublishProcess` 實例。|  
  
## <a name="remarks"></a>備註  
 `ICorPublishProcessEnum` 介面會實[ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。  
  
 `ICorPublishProcessEnum` 實例是由[ICorPublish：： EnumProcesses](icorpublish-enumprocesses-method.md)方法所建立。 `ICorPublishProcess` 物件集合的遍歷是以建立 `ICorPublishProcessEnum` 實例時所指定的篩選準則為基礎。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
