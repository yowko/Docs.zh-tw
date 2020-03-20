---
title: 可靠的安全設定檔
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144210"
---
# <a name="reliable-secure-profile"></a>可靠的安全設定檔

此示例演示如何組合 WCF 和[可靠安全設定檔 （RSP）。](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html) 此示例演示了["使連接](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf)通道"的實現，該通道可以與可靠消息一起組合，並選擇性地組成安全通道，以基於 RSP 規範創建可靠的安全綁定。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>討論區  
 此範例示範可靠的非同步雙向訊息交換案例。 此服務擁有雙工合約，而且用戶端會實作雙工回呼合約。 用戶端會向服務起始一個要求，這個要求預期在不同的連線上得到回應。 要求訊息是以可靠的方式傳送。 用戶端不想在其結尾開啟接聽端點。 因此，它會利用服務的「建立連線」要求輪詢服務，以便在這個「建立連線」要求的返回通道傳回回應。 此範例示範如何透過 HTTP 進行安全可靠的雙工通訊，而不讓用戶端公開接聽端點 (以及建立防火牆例外狀況)。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 打開**可靠的安全設定檔**解決方案。  
  
2. 按右鍵**解決方案資源管理器**中的**服務**專案 ，從內容功能表中選擇 **"調試****"，從內容功能表中啟動新實例**。 這會啟動服務主機。  
  
3. 按右鍵**解決方案資源管理器**中的**用戶端**專案 ，從內容功能表中選擇**調試**，**從內容功能表中啟動新實例**。 這會啟動用戶端。  
  
4. 在用戶端主控台視窗的提示中輸入任何字串，然後按一下 ENTER。這會將輸入字串傳送到服務，然後計算此字串的雜湊。  
  
5. 當服務回呼雙工回呼合約作業以顯示用戶端主控台視窗上的結果時，檢視用戶端視窗上的結果。 在服務上會有一個刻意的延遲，以模擬處理資料的長期作業。  
  
6. 監視 HTTP 流量 (透過 Network Monitor、Fiddler 等任何線上網路監視工具) 顯示通訊的順序是在可靠的安全設定檔制定之用戶端和服務之間建立的，並示範用戶端如何利用「建立連線」要求輪詢服務。 當服務準備好傳回處理過的回應時，它會使用最後一個「建立連線」要求的返回通道傳回結果。  
  
7. 在服務主控台視窗上按 ENTER 鍵，以關閉服務。 在用戶端主控台視窗上按 ENTER 鍵，以關閉用戶端。
