---
title: 可靠的安全設定檔
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
author: BrucePerlerMS
ms.openlocfilehash: 8bb7c6f9835fc7c0926e918563f85a28281f8a89
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073563"
---
# <a name="reliable-secure-profile"></a>可靠的安全設定檔
這個範例會示範如何撰寫 WCF 及[可靠的安全設定檔](https://go.microsoft.com/fwlink/?LinkId=178140)(RSP)。 這個範例會示範實作[建立連線](https://go.microsoft.com/fwlink/?LinkId=178141)通道可以使用來撰寫與可靠的傳訊，並選擇性地建立可靠的安全繫結的安全通道根據 RSP 規格。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>討論  
 此範例示範可靠的非同步雙向訊息交換案例。 此服務擁有雙工合約，而且用戶端會實作雙工回呼合約。 用戶端會向服務起始一個要求，這個要求預期在不同的連線上得到回應。 要求訊息是以可靠的方式傳送。 用戶端不想在其結尾開啟接聽端點。 因此，它會利用服務的「建立連線」要求輪詢服務，以便在這個「建立連線」要求的返回通道傳回回應。 此範例示範如何透過 HTTP 進行安全可靠的雙工通訊，而不讓用戶端公開接聽端點 (以及建立防火牆例外狀況)。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟**ReliableSecureProfile**解決方案。  
  
2.  以滑鼠右鍵按一下**服務**專案中**方案總管**，選取**偵錯**，**開始新執行個體**從內容功能表。 這會啟動服務主機。  
  
3.  以滑鼠右鍵按一下**用戶端**專案中**方案總管**，選取**偵錯**，**開始新執行個體**從內容功能表。 這會啟動用戶端。  
  
4.  在用戶端主控台視窗的提示中輸入任何字串，然後按一下 ENTER。這會將輸入字串傳送到服務，然後計算此字串的雜湊。  
  
5.  當服務回呼雙工回呼合約作業以顯示用戶端主控台視窗上的結果時，檢視用戶端視窗上的結果。 在服務上會有一個刻意的延遲，以模擬處理資料的長期作業。  
  
6.  監視 HTTP 流量 (透過 Network Monitor、Fiddler 等任何線上網路監視工具) 顯示通訊的順序是在可靠的安全設定檔制定之用戶端和服務之間建立的，並示範用戶端如何利用「建立連線」要求輪詢服務。 當服務準備好傳回處理過的回應時，它會使用最後一個「建立連線」要求的返回通道傳回結果。  
  
7.  在服務主控台視窗上按 ENTER 鍵，以關閉服務。 在用戶端主控台視窗上按 ENTER 鍵，以關閉用戶端。
