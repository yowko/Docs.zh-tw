---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: b03d141f1d2bfc18428c2f8651a340b789cfb995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
略過下一個列舉值會指示`celt`列舉中的項目，因此下次呼叫[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)不會傳回這些項目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
  
 [in]要略過的項目數目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT: 如果提供的項目數是 `celt`，則為 S_OK；否則為 S_FALSE。
