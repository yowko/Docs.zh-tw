---
title: 追蹤類型摘要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856006"
---
# <a name="trace-type-summary"></a>追蹤類型摘要
[來源層級](https://go.microsoft.com/fwlink/?LinkID=94943)會定義各種不同的追蹤層級：[重大]、[錯誤]、[警告]、[資訊] 和 [ `ActivityTracing`詳細資料]，以及提供旗標的描述，以切換追蹤界限與活動傳輸事件的輸出。  
  
 您也可以參閱[TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) ，以取得可從<xref:System.Diagnostics>發出的追蹤類型。  
  
 下表列出最重要的幾個。  
  
|追蹤類型|描述|  
|----------------|-----------------|  
|重大|嚴重錯誤或應用程式損毀。|  
|Error|可修復錯誤。|  
|警告|參考資訊。|  
|內容|非嚴重問題。|  
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
  
- 必須分別由「開始」和「停止」追蹤來開始與停止  
  
- 必須有「傳輸」追蹤緊接在「暫停」或「繼續」追蹤之前  
  
- 在「暫停」或「繼續」追蹤之間不可以有任何追蹤 (如果有這種追蹤的話)  
  
- 只要觀察到之前的條件，就可以有任意個嚴重/錯誤/警告/資訊/詳細資訊/傳輸追蹤  
  
 下列是定義全域範圍內理想活動的規則運算式：  
  
`R+`  
  
 其中 R 表示本機範圍內活動的規則運算式。 這會轉譯為：  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
