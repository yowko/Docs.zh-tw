---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053382"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
指示列舉值略過列舉中`celt`的下一個專案，讓下一次呼叫[IEnumRAWINPUTDEVIC： next](ienumrawinputdevic-next.md)不會傳回這些元素。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
  
 在要略過的元素數目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:如果提供的元素數目為， `celt`則為 S_OK;否則為 S_FALSE。
