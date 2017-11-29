---
title: "CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)
這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。  
  
 Windows Presentation Foundation (WPF) 基礎結構用於執行緒和 windows 的管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 pDispatchDelegate  
 指標`IDispatch`介面。  
  
 ppForwarder  
 位址指標`IDispatch`介面。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **DLL:**  
  
 在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll  
  
 在.NET Framework 4 和更新版本： PresentationHost_v0400.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [WPF Unmanaged API 參考](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
