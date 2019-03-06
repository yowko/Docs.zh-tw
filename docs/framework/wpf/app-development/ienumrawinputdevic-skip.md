---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: fadf7b5526598f446eb7e49640bf4d43ec7395bf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354514"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
指示列舉程式略過下一個`celt`列舉中的項目，因此下次呼叫[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)將不會傳回這些項目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
  
 [in]略過的項目數目。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:如果提供的項目數目，為 S_OK `celt`;否則為 S_FALSE。
