---
title: ICorPublishAppDomainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790669"
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum 介面
[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽目前存在於進程中的[ICorPublishAppDomain](icorpublishappdomain-interface.md)物件集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icorpublishappdomainenum-next-method.md)|從目前位置開始，取得集合中指定數目的 `ICorPublishAppDomain` 實例。|  
  
## <a name="remarks"></a>備註  
 `ICorPublishAppDomainEnum` 介面會實[ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
