---
title: StrongNameErrorInfo 函式
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
ms.openlocfilehash: dd83fc6a7f553b54cc2acd5e9a93d8d58747d75a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141710"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 函式
取得由其中一強式名稱函式所引發的最後一個錯誤代碼。  
  
 這個函數已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>傳回值  
 其中一個強式名稱函數所設定的最後一個 COM 錯誤碼。  
  
## <a name="remarks"></a>備註  
 大部分的強式名稱方法會傳回簡單的 `true`，或 `false` 表示成功完成。 使用 `StrongNameErrorInfo` 函式來抓取 HRESULT，以指定強式名稱函數所產生的最後一個錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
