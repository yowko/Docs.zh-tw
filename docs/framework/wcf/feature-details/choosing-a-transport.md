---
title: 選擇傳輸
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b051cdeebf83b34b6e503d8d9cb54a38a46a2a6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="choosing-a-transport"></a>選擇傳輸
本主題將說明選擇 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中包含的三種主要傳輸的準則：HTTP、TCP 和具名管道。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也包括訊息佇列 (亦稱為 MSMQ) 傳輸，但是本文件不討論訊息佇列。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 程式設計模型會分開端點作業 (如服務合約中所示) 和連接兩個端點的傳輸機制。 如此可為您提供彈性以決定如何向網路公開您的服務。  
  
 在[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，指定如何跨網路傳輸資料所使用的端點之間*繫結*，這由所組成的序列*繫結項目*。 傳輸是由傳輸繫結項目表示，它是繫結的一部分。 繫結包含選擇性通訊協定繫結項目 (例如安全性)、必要的訊息編碼器繫結項目和必要的傳輸繫結項目。 傳輸會傳送或接收來往另一個應用程式之訊息的序列化形式。  
  
 如果您必須連線至現有的用戶端或伺服器，可能無法選擇使用特定的傳輸。 然而，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可透過多個端點來存取，每個端點都有不同的傳輸。 當單一傳輸未涵蓋您服務的目標對象時，請考慮在多個端點上公開服務。 然後用戶端應用程式可以使用最適合的端點。  
  
 在選擇傳輸之後，您必須選取使用它的繫結。 您可以選擇系統提供的繫結 (請參閱[之繫結](../../../../docs/framework/wcf/system-provided-bindings.md))，或者您可以建立您自己的自訂繫結 (請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md))。 您也可以建立自己的繫結。 如需詳細資訊，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
## <a name="advantages-of-each-transport"></a>各種傳輸的優點  
 本節將說明選擇這三種主要傳輸其中之一的主要原因，包括進行選擇的詳細決策圖表。  
  
### <a name="when-to-use-http-transport"></a>使用 HTTP 傳輸的時機  
 HTTP 是用戶端和伺服器之間的要求/回應通訊協定。 最常用的應用程式是由使用 Web 伺服器進行通訊的 Web 瀏覽器用戶端所組成的。 用戶端會將要求傳送至伺服器，接聽用戶端要求訊息。 當伺服器收到要求時，會傳回一個回應，其中包含要求的狀態。 如果成功，會傳回選擇性資料 (例如網頁、錯誤訊息或其他資訊)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] HTTP 通訊協定，請參閱[HTTP-超文字傳輸通訊協定](http://go.microsoft.com/fwlink/?LinkId=94858)。  
  
 HTTP 通訊協定不是以連線為基礎，一旦傳送回應，便不會維護狀態。 若要處理多頁交易，應用程式必須持續必要的狀態。  
  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，HTTP 傳輸繫結已針對與舊版非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 系統的互通性最佳化。 如果所有的通訊方都是使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，TCP 或具名管道繫結會更快。 如需詳細資訊，請參閱 <xref:System.ServiceModel.NetTcpBinding> 與 <xref:System.ServiceModel.NetNamedPipeBinding>。  
  
### <a name="when-to-use-the-tcp-transport"></a>使用 TCP 傳輸的時機  
 TCP 是以連線為基礎、以資料流為導向的傳遞服務，具有端對端錯誤偵測和更正。 *連接為基礎*表示主機之間的通訊工作階段會交換資料之前建立。 主機是由邏輯 IP 位址所識別的 TCP/IP 網路上的裝置。  
  
 TCP 提供可靠的資料傳遞且使用簡易。 特別是，TCP 會通知傳送者有封包傳遞、保證封包會以和傳送時相同的順序傳遞、重新傳輸遺失的封包，以及確保資料封包沒有重複。 請注意，這個可靠的傳遞適用於兩個 TCP/IP 節點之間，而且不是相同的動作*WS-SECURITY 與 Ws-reliablemessaging*套用端點之間，無論多少中繼節點可能包括。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] TCP 傳輸已針對通訊兩端均使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]的案例最佳化。 這個繫結對於包含不同電腦之間通訊的案例而言，是最快的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結。 訊息交換會對最佳化訊息傳輸使用 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>。 TCP 提供雙工通訊，因此即使用戶端位於網路位址轉譯 (NAT) 後，仍可用於實作雙工合約。  
  
### <a name="when-to-use-the-named-pipe-transport"></a>使用具名管道傳輸的時機  
 具名管道是 Windows 作業系統核心中的物件，例如處理程序可用於通訊之共用記憶體的區段。 具名管道有名稱，且可以用於單一電腦上處理程序之間的單向或雙工通訊。  
  
 當單一電腦上的不同 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式之間需要通訊，而您想要防止與其他電腦進行通訊時，請使用具名管道傳輸。 另一項限制是從「Windows 遠端桌面」執行的處理程序可能會受到相同的「Windows 遠端桌面」工作階段的限制，除非它們有更高的權限。  
  
> [!WARNING]
>  當使用弱式萬用字元 URL 保留項目在 IIS 中裝載的多個站台上的具名的管道傳輸，可能會發生下列錯誤： 時發生錯誤的啟動服務 'NetPipeActivator' 通訊協定 'net.pipe' 嘗試監聽網站 '2'因此通訊協定已暫時停用站台。 請參閱例外狀況訊息，如需詳細資訊。 URL: Weakwildcard\<機器名稱 > / 狀態： ConflictingRegistration 例外狀況： 處理序名稱： SMSvcHost 處理序識別碼： 1076 \  
  
## <a name="decision-points-for-choosing-a-transport"></a>選擇傳輸的決策點  
 下表說明用於選擇傳輸的常見決策點。 建議您考慮適用於您應用程式的其他屬性和傳輸。 請辨識對您應用程式很重要的屬性，辨識與您各個屬性有正面關聯的傳輸，然後選擇最適合您屬性組的傳輸。  
  
|屬性|描述|偏好的傳輸|  
|---------------|-----------------|------------------------|  
|診斷|Diagnostics 可讓您自動偵測傳輸連接問題。 所有的傳輸都支援傳回說明連接之錯誤資訊的能力。 然而，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不包括調查網路問題的診斷工具。|無|  
|裝載|所有的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點都必須裝載在應用程式內。 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 及更早版本只支援使用 HTTP 傳輸的裝載應用程式。 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，已新增對於裝載所有 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳輸的支援，包括 TCP 和具名管道。 如需詳細資訊，請參閱[裝載在 Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)和[Windows Process Activation Service 中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。|HTTP|  
|檢閱|Inspection 是在傳輸期間從訊息擷取及處理資訊的能力。 HTTP 通訊協定會分開路由及控制資訊與資料，讓它更容易建立檢查及分析訊息的工具。 容易檢查的傳輸在網路應用裝置中可能也需要較少的處理能力。 所使用的安全性層級會影響是否可以檢查訊息。|HTTP|  
|Latency|Latency 是完成訊息交換所需要的最小時間量。 所有的網路作業多少都會有延遲時間，視所選擇的傳輸而定。 與原生訊息交換模式為要求/回覆的傳輸 (例如 HTTP) 使用雙工或單向通訊，會因訊息的強制關聯造成額外的延遲時間。 在這種情況中，請考慮使用原生訊息交換模式為雙工的傳輸，例如 TCP。|TCP、具名<br /><br /> 管道|  
|Reach|傳輸的範圍反映出傳輸與其他系統連線時的功能。 具名管道傳輸的範圍非常小；它只能連至在相同電腦上執行的服務。 TCP 和 HTTP 傳輸都有極佳的範圍，而且可以穿透某些 NAT 和防火牆組態。 如需詳細資訊，請參閱[使用 Nat 與防火牆](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)。|HTTP、TCP|  
|安全性|Security 是在傳輸期間藉由提供機密性、完整性或驗證來保護訊息的能力。 機密性可保護訊息不受檢查，完整性可保護訊息不受修改，而驗證可提供有關訊息的傳送者或接收者的保證。<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援訊息層級和傳輸層級的傳輸安全性。 如果傳輸支援緩衝傳輸模式，訊息安全性便會以該傳輸組成。 傳輸安全性的支援會依所選擇的傳輸而有所不同。 HTTP、TCP 和具名管道傳輸在傳輸安全性的支援中，有合理的同位檢查。|全部|  
|輸送量|Throughput 是測量可以在指定的時間內傳輸及處理的資料量。 和延遲時間一樣，所選擇的傳輸會影響服務作業的輸送量。 將傳輸的輸送量最大化需要最小化傳輸內容的額外負荷，以及最小化等待訊息交換完成所花費的時間。 TCP 和具名管道傳輸都會為訊息本文增加少許額外負荷，並支援減少等候訊息回覆時間的原生雙工類型。|TCP、具名管道|  
|Tooling|Tooling 代表開發、診斷、裝載和其他活動之通訊協定的協力廠商應用程式支援。 開發搭配 HTTP 通訊協定使用的工具和軟體代表極大的投資。|HTTP|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
  <<!--zz <xref:System.ServiceModel.WsDualHttpBinding> --> `System.ServiceModel.WsDualHttpBinding`
 <<!--zz <xref:System.ServiceModel.WsFederationHttpBinding>  --> `System.ServiceModel.WsFederationHttpBinding` <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 [繫結](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [建立使用者定義繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
