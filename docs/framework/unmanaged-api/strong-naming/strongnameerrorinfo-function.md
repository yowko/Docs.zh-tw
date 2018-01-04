---
title: "StrongNameErrorInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameErrorInfo
helpviewer_keywords: StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81e6eaa83baab67f54a1b1ce46d616be7e6fdd62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 函式
取得其中一個強式名稱的函式所引發的最後一個錯誤碼。  
  
 此函式已被取代。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>傳回值  
 最後一個 COM 錯誤碼的強式名稱的函式的其中一個來設定。  
  
## <a name="remarks"></a>備註  
 大部分的強式名稱的方法會傳回簡單`true`或`false`成功完成的指示。 使用`StrongNameErrorInfo`函式來擷取指定強式名稱的函式所產生的最後一個錯誤的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [強式命名全域靜態函式](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)
