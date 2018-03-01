---
title: IEnumRAWINPUTDEVIC:Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af6cb5bfe07923e13f1b76c785d830a9af15eaf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
列舉的下一步 `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)中列舉值的清單中，傳回其結構`rgelt`列舉中的項目實際數目以及`pceltFetched`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
  
 [in]數目[RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)中傳回的結構`rgelt`。  
  
 `rgelt`  
  
 [out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。  
  
 `pceltFetched`  
  
 [out] 指向 `rgelt` 中實際提供項目數的指標。 如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT: 如果提供的項目數是 `celt`，則為 S_OK；否則為 S_FALSE。
