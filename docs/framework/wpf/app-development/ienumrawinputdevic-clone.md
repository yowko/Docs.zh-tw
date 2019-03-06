---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: a4c5e7db813089d1dd138416ac54dd4be467b87b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355013"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>參數  
 `ppenum`  
  
 [out]收到的輸出變數位址[IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)介面指標。 如果方法不成功，這個輸出變數的值會是未定義。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:這個方法支援標準傳回值 E_INVALIDARG、 E_OUTOFMEMORY，以及 E_UNEXPECTED。  
  
## <a name="remarks"></a>備註  
 這個方法可讓您能夠記錄列舉序列中的點，才能在稍後返回該時間點。 呼叫端必須釋放這個新的列舉值，分別從第一個列舉值。
