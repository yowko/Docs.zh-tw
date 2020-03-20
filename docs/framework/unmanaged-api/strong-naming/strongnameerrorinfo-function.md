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
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176938"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 函式
取得由其中一強式名稱函式所引發的最後一個錯誤代碼。  
  
 此函數已被棄用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>傳回值  
 由強式名稱函數之一設置的最後一個 COM 錯誤代碼。  
  
## <a name="remarks"></a>備註  
 大多數強式名稱方法返回成功完成的簡單`true`或`false`指示。 使用`StrongNameErrorInfo`函數檢索指定強式名稱函數生成的最後一個錯誤的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
