---
title: 封送處理字串
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db33d59d1fc1c19e07567108970db77059cebb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223026"
---
# <a name="marshaling-strings"></a>封送處理字串
平台叫用會複製字串參數，並視需要從 .NET Framework 格式 (Unicode) 轉換成 Unmanaged 格式 (ANSI)。 傳回函式時，因為 Managed 字串不可變，所以平台叫用不會將 Managed 字串從 Unmanaged 記憶體複製回 Managed 記憶體。  
  
 下表列出字串的封送處理選項，並描述其用法，以及提供對應 .NET Framework 範例的連結。  
  
|String|說明|範例|  
|------------|-----------------|------------|  
|傳值。|將字串傳遞為 In 參數。|[MsgBox](msgbox-sample.md)|  
|作為結果。|從 Unmanaged 程式碼傳回字串。|[字串](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|傳址。|使用 <xref:System.Text.StringBuilder> 將字串傳遞為 In/Out 參數。|[緩衝區](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|在傳值結構中。|透過本身為 In 參數的結構傳遞字串。|[結構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|在傳址結構中 **(char\*)**。|透過本身為 In/Out 參數的結構傳遞字串。 Unmanaged 函式需要字元緩衝區的指標，而且緩衝區大小是結構的成員。|[字串](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|在傳址結構中 **(char[])**。|透過本身為 In/Out 參數的結構傳遞字串。 Unmanaged 函式需要內嵌的字元緩衝區。|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|在傳值類別中 **(char\*)**。|在類別中傳遞字串 (類別是 In/Out 參數)。 Unmanaged 函式需要字元緩衝區的指標。|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|在傳值類別中 **(char[])**。|在類別中傳遞字串 (類別是 In/Out 參數)。 Unmanaged 函式需要內嵌的字元緩衝區。|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|作為傳值字串陣列。|建立以傳值方式傳遞的字串陣列。|[陣列](marshaling-different-types-of-arrays.md)|  
|作為包含傳值字串的結構陣列。|建立包含字串的結構陣列，並以傳值方式傳遞該陣列。|[陣列](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>另請參閱

- [使用平台叫用封送處理資料](marshaling-data-with-platform-invoke.md)
- [封送處理類別、結構和等位](marshaling-classes-structures-and-unions.md)
- [封送處理不同類型的陣列](marshaling-different-types-of-arrays.md)
- [其他封送處理範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
