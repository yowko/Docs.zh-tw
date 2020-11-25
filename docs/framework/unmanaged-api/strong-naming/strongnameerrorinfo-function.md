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
ms.openlocfilehash: 90abfcd573795ae529714e21b13f90d6e15c7dad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732264"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 函式

取得由其中一強式名稱函式所引發的最後一個錯誤代碼。  
  
 此函數已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>傳回值  

 其中一個強式名稱函式所設定的最後一個 COM 錯誤碼。  
  
## <a name="remarks"></a>備註  

 大部分強式名稱方法會傳回簡單 `true` 或 `false` 表示成功完成。 使用函 `StrongNameErrorInfo` 式來取出 HRESULT，以指定強式名稱函式所產生的最後一個錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
