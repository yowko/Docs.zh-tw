---
title: ICorPublish::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790760"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses 方法
取得在這部電腦上執行之 managed 進程的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `Type`  
 [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md)列舉的值，指定要抓取的進程類型。 在目前的版本中，只有 COR_PUB_MANAGEDONLY 有效。  
  
 `ppIEnum`  
 [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)實例位址的指標，這是進程的列舉值。  
  
## <a name="remarks"></a>備註  
 列舉值的進程集合是以呼叫 `EnumProcesses` 方法時正在執行之進程的快照集為基礎。 列舉值不會包含呼叫 `EnumProcesses` 之後終止或啟動的任何進程。  
  
 可以在這個[ICorPublish](icorpublish-interface.md)實例上多次呼叫 `EnumProcesses` 方法，以建立最新的進程集合。 `EnumProcesses` 方法的後續呼叫將不會影響現有的集合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorPublish 介面](icorpublish-interface.md)
