---
title: Net.TCP Port Sharing
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: b04266b15f786e3a5a93ac1e9fff1754c397ccd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762747"
---
# <a name="nettcp-port-sharing"></a>Net.TCP Port Sharing
Windows Communication Foundation (WCF) 的高效能通訊提供全新的 TCP 架構網路通訊協定 (net.tcp://)。 WCF 也引進全新的系統元件，可讓多個使用者處理序共用 net.tcp 連接埠的 Net.TCP Port Sharing Service。  
  
## <a name="background-and-motivation"></a>源起與動機  
 TCP/IP 通訊協定最初問世時，只有少數的應用程式通訊協定會使用它。 TCP/IP 藉由將唯一的 16 位元連接埠號碼指派給每個應用程式通訊協定，以便透過連接埠號碼來區分各個應用程式。 例如，今日的 HTTP 流量已經過標準化使用 TCP 連接埠 80，而 SMTP 則是使用 TCP 連接埠 25，另外 FTP 則是使用 TCP 連接埠 20 和 21。 其他使用 TCP 做為傳輸的應用程式可以依照慣例或是透過正式標準化作業來選擇其他可用的連接埠號碼。  
  
 使用連接埠號碼來區分應用程式具有安全上的問題。 一般我們會設定防火牆來攔截所有連接埠上的 TCP 流量 (除了少數幾個熟知的進入點之外)，因此部署一個使用非標準連接埠的應用程式常常會因為企業與個人防火牆的緣故而變得很複雜，甚至不可能辦到。 透過標準、已知且已經允許的連接埠進行通訊的應用程式會降低外部攻擊面積。 許多網路應用程式會運用 HTTP 通訊協定，因為大部分的防火牆設定預設會允許 TCP 連接埠 80 上的流量。  
  
 在 HTTP.SYS 模型中，許多不同的 HTTP 應用程式流量在經過多工處理後，可以傳入單一 TCP 連接埠，而這已經變成了 Windows 平台的標準做法。 這種做法提供防火牆管理員一個共同的控制點，同時讓應用程式開發人員在建置可以運用網路的新應用程式時，將部署成本降到最低。  
  
 在多個 HTTP 應用程式之間共用連接埠的能力，一直都是網際網路資訊服務 (IIS) 的標準功能之一。 但是，一直到 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 引進了 HTTP.SYS (核心模式 HTTP 通訊協定接聽項) 之後，才讓這項基礎結構全面普及化。 事實上，HTTP.SYS 可讓任意使用者處理序共用專門用來處理 HTTP 流量的 TCP 連接埠。 這項功能可讓許多 HTTP 應用程式共存於同一部實體電腦內個別、隔離的處理序中，同時透過 TCP 連接埠 80 共用所需的網路基礎結構以便傳送與接收流量。 Net.TCP 連接埠共用服務可讓 net.tcp 應用程式共用同樣類型的連接埠。  
  
## <a name="port-sharing-architecture"></a>連接埠共用架構  
 在 WCF 中的連接埠共用架構有三個主要元件：  
  
- 工作者處理序：任何透過 net.tcp:// 使用共用連接埠進行通訊的程序。  
  
- WCF TCP 傳輸：實作 net.tcp:// 通訊協定。  
  
- Net.TCP Port Sharing Service:可讓許多背景工作處理序共用相同的 TCP 連接埠。  
  
 Net.TCP 連接埠共用服務一項使用者模式的 Windows 服務，可代表透過它進行連線的背景工作處理序接受 net.tcp:// 連線。 當通訊端連線抵達時，連接埠共用服務就會檢查傳入的訊息資料流以取得其目的地位址。 連接埠共用服務會根據這個位址，將資料流路由至最終會處理資料的應用程式中。  
  
 當使用 net.tcp:// 連接埠共用開啟的 WCF 服務時，WCF TCP 傳輸基礎結構不會直接開啟 TCP 通訊端應用程式處理序中。 反之，傳輸基礎結構會將服務的基底位址統一資源識別元 (URI) 註冊到 Net.TCP 連接埠共用服務，並等候連接埠共用服務代表自己接聽訊息。  連接埠共用服務會在訊息抵達時，將目的地為應用程式服務的訊息分派出去。  
  
## <a name="installing-port-sharing"></a>安裝連接埠共用  
 儘管所有支援 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 的作業系統都可使用 Net.TCP 連接埠共用服務，但是預設不會啟用此服務。 為了安全起見，第一次使用 Net.TCP 連接埠共用服務前，系統管理員必須先手動加以啟用。 Net.TCP Port Sharing Service 會公開組態選項，讓您操控連接埠共用服務所擁有的數個網路通訊端特徵。 如需詳細資訊，請參閱[如何：啟用 Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)。  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>在應用程式中使用 Net.tcp Port Sharing  
 使用 net.tcp:// 連接埠共用 WCF 應用程式中的最簡單方式是公開服務，使用<xref:System.ServiceModel.NetTcpBinding>並啟用 Net.TCP Port Sharing Service 使用<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A>屬性。  
  
 如需這個做法的詳細資訊，請參閱[如何：設定 WCF 服務，以使用連接埠共用](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)。  
  
## <a name="security-implications-of-port-sharing"></a>連接埠共用的安全性含意  
 儘管 Net.TCP 連接埠共用服務會在應用程式與網路之間提供一層處理，您還是應該將使用連接埠共用的應用程式視為直接在網路上接聽一樣來加以保護。 具體來說，使用連接埠共用的應用程式應該評估執行時所需的處理序權限。 請考慮使用內建的網路服務帳戶來執行應用程式，在此情況下會以網路通訊所需的最低處理序權限來執行。  
  
## <a name="see-also"></a>另請參閱

- [設定 Net.TCP 連接埠共用服務](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [裝載](../../../../docs/framework/wcf/feature-details/hosting.md)
- [如何：設定 WCF 服務，以使用連接埠共用](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [如何：啟用 Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
