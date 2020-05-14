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
ms.openlocfilehash: 70255a89cee13abfe63b01351f8ffba51e54665a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396395"
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
 列舉值的進程集合是以呼叫方法時執行的進程快照集為基礎 `EnumProcesses` 。 列舉值不會包含在呼叫之前或開始之前終止的任何進程 `EnumProcesses` 。  
  
 可以 `EnumProcesses` 在這個[ICorPublish](icorpublish-interface.md)實例上多次呼叫方法，以建立新的最新進程集合。 方法的後續呼叫將不會影響現有的集合 `EnumProcesses` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorPublish 介面](icorpublish-interface.md)
