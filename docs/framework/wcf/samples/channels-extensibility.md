---
title: 通道擴充性
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 1a734c305e2a6f2fc759647ab5bdf380f7c7eeee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253830"
---
# <a name="channels-extensibility"></a>通道擴充性

本節包含示範自訂通道的範例。  
  
## <a name="in-this-section"></a>本節內容  

 [本機通道](local-channel.md)  
 示範本機通道，這是用於相同應用程式域內通訊的 WCF 傳輸通道。  
  
 [可靠的安全設定檔](reliable-secure-profile.md)  
 示範如何撰寫 WCF 和可靠的安全設定檔 (RSP) 。  
  
 [自訂通道發送器](custom-channel-dispatcher.md)  
 示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。  
  
 [區塊處理通道](chunking-channel.md)  
 示範如何限制用來緩衝使用 WCF 傳送之大型訊息的記憶體數量。
  
 [HttpCookieSession](httpcookiesession.md)  
 示範如何將自訂通訊協定通道建置成在工作階段管理使用 HTTP Cookie。  
  
 [自訂訊息攔截器](custom-message-interceptor.md)  
 示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。
