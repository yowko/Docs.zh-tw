---
title: "封送處理字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d53cd4072ab3f9ff52729f122c0a0ecab400df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-strings"></a>封送處理字串
平台叫用會複製字串參數，並視需要從 .NET Framework 格式 (Unicode) 轉換成 Unmanaged 格式 (ANSI)。 傳回函式時，因為 Managed 字串不可變，所以平台叫用不會將 Managed 字串從 Unmanaged 記憶體複製回 Managed 記憶體。  
  
 下表列出字串的封送處理選項，並描述其用法，以及提供對應 .NET Framework 範例的連結。  
  
|String|描述|範例|  
|------------|-----------------|------------|  
|傳值。|將字串傳遞為 In 參數。|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|作為結果。|從 Unmanaged 程式碼傳回字串。|[字串](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|傳址。|使用 <xref:System.Text.StringBuilder> 將字串傳遞為 In/Out 參數。|[緩衝區](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|在傳值結構中。|透過本身為 In 參數的結構傳遞字串。|[結構](http://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|在傳址結構中 **(char\*)**。|透過本身為 In/Out 參數的結構傳遞字串。 Unmanaged 函式需要字元緩衝區的指標，而且緩衝區大小是結構的成員。|[字串](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|在傳址結構中 **(char[])**。|透過本身為 In/Out 參數的結構傳遞字串。 Unmanaged 函式需要內嵌的字元緩衝區。|[OSInfo](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|在傳值類別中 **(char\*)**。|在類別中傳遞字串 (類別是 In/Out 參數)。 Unmanaged 函式需要字元緩衝區的指標。|[OpenFileDlg](http://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|在傳值類別中 **(char[])**。|在類別中傳遞字串 (類別是 In/Out 參數)。 Unmanaged 函式需要內嵌的字元緩衝區。|[OSInfo](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|作為傳值字串陣列。|建立以傳值方式傳遞的字串陣列。|[陣列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|作為包含傳值字串的結構陣列。|建立包含字串的結構陣列，並以傳值方式傳遞該陣列。|[陣列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>請參閱  
 [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [平台叫用資料類型](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [封送處理類別、結構和等位](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [封送處理類型的陣列](http://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [其他封送處理範例](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)
