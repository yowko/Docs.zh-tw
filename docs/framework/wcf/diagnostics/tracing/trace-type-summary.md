---
title: 追蹤類型摘要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403839"
---
# <a name="trace-type-summary"></a>追蹤類型摘要
[來源層級](https://go.microsoft.com/fwlink/?LinkID=94943)定義不同的追蹤層級： 嚴重、 錯誤、 警告、 資訊和詳細資訊，並提供描述`ActivityTracing`旗標，它的輸出會切換追蹤界限與活動傳輸事件。  
  
 您也可以檢閱[TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169)可以從發出的追蹤類型<xref:System.Diagnostics>。  
  
 下表列出最重要的幾個。  
  
|追蹤類型|描述|  
|----------------|-----------------|  
|Critical|嚴重錯誤或應用程式損毀。|  
|錯誤|可修復錯誤。|  
|警告|告知性訊息。|  
|資訊|非嚴重問題。|  
|詳細資訊|偵錯追蹤。|  
|啟動|開始邏輯處理單位。|  
|暫止|暫停邏輯處理單位。|  
|繼續|繼續邏輯處理單位。|  
|停止|停止邏輯處理單位。|  
|傳輸|相互關聯身分識別變更。|  
  
 活動會定義為上述追蹤類型的組合。  
  
 下列是定義本機 (追蹤來源) 範圍內理想活動的規則運算式：  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 這表示活動必須滿足下列條件。  
  
-   必須分別由「開始」和「停止」追蹤來開始與停止  
  
-   必須有「傳輸」追蹤緊接在「暫停」或「繼續」追蹤之前  
  
-   在「暫停」或「繼續」追蹤之間不可以有任何追蹤 (如果有這種追蹤的話)  
  
-   只要觀察到之前的條件，就可以有任意個嚴重/錯誤/警告/資訊/詳細資訊/傳輸追蹤  
  
 下列是定義全域範圍內理想活動的規則運算式：  
  
```  
R+   
```  
  
 其中 R 表示本機範圍內活動的規則運算式。 這會轉譯為：  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
