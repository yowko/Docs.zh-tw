---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545335"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>參數  
 `ppenum`  
  
 [out]收到的輸出變數的位址[IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)介面指標。 如果此方法不成功，這個輸出變數的值未定義。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT： 這個方法支援標準傳回值 E_INVALIDARG、 E_OUTOFMEMORY，以及 E_UNEXPECTED。  
  
## <a name="remarks"></a>備註  
 這個方法可將列舉序列中記錄點，以便在稍後返回該點。 呼叫端必須釋放這個新的列舉值，分別從第一個列舉值。
