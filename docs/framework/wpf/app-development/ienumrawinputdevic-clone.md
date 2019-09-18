---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053412"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>參數  
 `ppenum`  
  
 脫銷接收[IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)介面指標的輸出變數位址。 如果方法不成功，這個輸出變數的值會是未定義的。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:這個方法支援標準傳回值 E_INVALIDARG、E_OUTOFMEMORY 和 E_UNEXPECTED。  
  
## <a name="remarks"></a>備註  
 這個方法可以記錄列舉序列中的點，以便稍後再返回該點。 呼叫端必須與第一個列舉值分開發行這個新的列舉值。
