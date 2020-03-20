---
title: 追蹤類型摘要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674832"
---
# <a name="trace-type-summary"></a>追蹤類型摘要
[源級別](xref:System.Diagnostics.SourceLevels)定義各種跟蹤級別：嚴重、錯誤、警告、資訊和詳細，並提供`ActivityTracing`標誌的說明，該標誌可切換跟蹤邊界和活動傳輸事件的輸出。  
  
 您還可以查看<xref:System.Diagnostics.TraceEventType>可以從 中釋放的跟蹤類型<xref:System.Diagnostics>。  
  
 下表列出最重要的幾個。  
  
|追蹤類型|描述|  
|----------------|-----------------|  
|重大|嚴重錯誤或應用程式損毀。|  
|錯誤|可修復錯誤。|  
|警告|參考資訊。|  
|資訊|非嚴重問題。|  
|「詳細資訊」|偵錯追蹤。|  
|Start|開始邏輯處理單位。|  
|暫止|暫停邏輯處理單位。|  
|繼續|繼續邏輯處理單位。|  
|Stop|停止邏輯處理單位。|  
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
