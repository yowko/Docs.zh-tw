---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d40d1799a7c1572e8213fda3a163fb9a84060f92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle 方法
取得已回收控制代碼指定的受管理物件的參考指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `handle`  
 [in]具有記憶體回收控制代碼的 managed 物件指標。 這個值是<xref:System.IntPtr>物件，並可從擷取<xref:System.Runtime.InteropServices.GCHandle>針對受管理的物件。  
  
 `pOutValue`  
 [out]ICorDebugReferenceValue 物件，代表指定之 managed 物件的參考的位址指標。  
  
## <a name="remarks"></a>備註  
 請勿混淆傳回的參考值，與記憶體回收集合參考值。  
  
 傳回的參考行為就像一般的參考。 當在中斷點後繼續執行程式碼時，它會停用。 目標物件的存留期間不會受到參考值的存留期。  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle`方法不會驗證此控制代碼。 因此，`GetReferenceValueFromGCHandle`方法可能會毀損偵錯工具和程式碼進行偵錯，如果傳遞無效的控制代碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
