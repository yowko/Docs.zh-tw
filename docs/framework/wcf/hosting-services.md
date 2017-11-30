---
title: "裝載服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0d3cd2f53b81ae6114baa3c7eedd899126ed579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-services"></a>裝載服務
如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務是設計為在支援 Managed 程式碼的 Windows 處理序中執行的。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 為服務導向應用程式的建置提供了統一的程式設計模型。 這個程式設計模型會維持一致並與部署服務的執行階段環境互相獨立。 實務上，這意味著不管裝載選項為何，服務的程式碼看起來都差不多。  
  
 這些裝載選項的範圍從在主控台應用程式中執行到伺服器環境 (例如，在由網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 管理的背景工作處理序中執行的 Windows 服務) 不一而足。 開發人員可選擇滿足服務部署需求的裝載環境。 這些需求可能源自部署了應用程式的平台、應用程式必須賴以傳送與接收訊息的傳輸，或是用來確保足夠可用性所需的處理序回收類型與其他處理序管理，或是其他一些管理或可靠性需求。 下節將提供有關裝載選項的資訊與指引。  
  
## <a name="hosting-options"></a>裝載選項  
  
#### <a name="self-hosting-in-a-managed-application"></a>在 Managed 應用程式中自我裝載  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務可以裝載於任何 Managed 應用程式。 這是最彈性的選項，因為它只需要最少的基礎結構就可部署。 您可以將服務的程式碼嵌入 Managed 應用程式程式碼中，然後建立並開啟 <xref:System.ServiceModel.ServiceHost> 的執行個體以便提供服務。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][How to： 將 WCF 服務裝載於 Managed 應用程式](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。  
  
 此選項可啟用兩個常見的案例：在主控台應用程式與豐富型用戶端 (Rich Client) 應用程式 (例如，以 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 或 Windows Forms (WinForms) 為基礎的應用程式) 中執行的 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 服務。 在應用程式開發階段，於主控台應用程式中裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務一般來說是很有用的方式。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。 這個裝載選項同時可讓豐富型用戶端應用程式 (例如， [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 和 WinForms 應用程式) 更容易與外界通訊。 例如，使用 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 做為使用者介面，並同時裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務以允許其他用戶端與其連線並共用資訊的對等共同作業用戶端。  
  
#### <a name="managed-windows-services"></a>Managed Windows 服務  
 這個裝載選項包含可將 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務裝載為 Managed Windows 服務 (之前稱為 NT 服務) 的註冊應用程式定義域 (AppDomain)，如此一來便可透過 Windows 服務的服務控制管理員 (SCM) 來控制服務的處理序存留期。 就像自我裝載選項一樣，此類型的裝載環境要求將某些裝載程式碼撰寫成應用程式的一部分。 此服務可同時實作為 Windows 服務以及 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，方法是讓它繼承 <xref:System.ServiceProcess.ServiceBase> 類別以及 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務合約介面。 <xref:System.ServiceModel.ServiceHost> 接著會透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 方法來建立並開啟，並透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法加以關閉。 繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別必須同時實作，以允許藉由 Installutil.exe 工具將程式安裝為 Windows 服務。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][How to： 將 WCF 服務裝載於 Managed 的 Windows 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)。 Managed Windows 服務裝載選項所啟用的案例，就是在非訊息啟動的安全環境中由 IIS 外部所裝載的長期執行之 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務案例。 服務的存留期會改由作業系統來控制。 所有 Windows 版本都提供這個裝載選項。  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 IIS 裝載選項會與 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 整合並使用這些技術所提供的功能，例如處理序回收、閒置關機、處理序健康狀態監控，以及訊息啟動。 在 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 作業系統中，建議您採用這個解決方案來裝載必須具備高度可用性與高度擴充性的 Web 服務應用程式。 IIS 同時提供整合式管理功能，而這也是客戶希望從企業級伺服器產品中所得到的功能。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] 如何為 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務設定 IIS 裝載的詳細資訊，請參閱 [How to: Host a WCF Service in IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 請注意，IIS 裝載的服務只能使用 HTTP 傳輸。 它在 IIS 5.1 版的實作方式已經為 [!INCLUDE[wxp](../../../includes/wxp-md.md)]帶來一些限制。 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中，IIS 5.1 為 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 服務所提供的訊息啟用會封鎖相同電腦上其他所有自我裝載的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，不讓這些服務使用連接埠 80 來進行通訊。 在[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中，當 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 服務透過 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]來裝載時，可以在其他應用程式的相同的 AppDomain/應用程式集區/背景工作處理序中執行。 但是由於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 和 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 都採用核心模式 HTTP 堆疊 (HTTP.sys)，因此 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 可與其他在相同電腦上執行的自我裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務共用連接埠 80 (如果是 IIS 5.1 就不能這麼做)。  
  
#### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)  
 Windows Process Activation Service (WAS) 是 [!INCLUDE[lserver](../../../includes/lserver-md.md)] 上全新的處理序啟動機制 ( [!INCLUDE[wv](../../../includes/wv-md.md)]也提供此機制)。 它包含熟悉的 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 處理序模型 (應用程式集區和訊息處理序啟用) 和裝載功能 (例如，快速故障防護、健康狀態監控，與回收機制)，但是從啟用架構中移除對 HTTP 的相依性。 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 會使用 WAS，以完成透過 HTTP 的訊息啟用。 其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 元件也可外掛至 WAS 以提供 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 所支援的其他通訊協定 (例如 TCP、MSMQ，與具名管道) 上的訊息啟動。 如此便可讓使用通訊協定的應用程式使用 IIS 功能，例如處理序回收、快速故障防護，以及只提供給以 HTTP 為基礎的應用程式使用的常見組態系統等。  
  
 這個裝載選項要求必須正確設定 WAS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] 如何設定 WAS 裝載的詳細資訊，請參閱 [How to: Host a WCF Service in WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>選擇裝載環境  
 下表將摘要說明一些與各個裝載選項相關的主要優點與案例。  
  
|裝載環境|常見案例|主要優點與限制|  
|-------------------------|----------------------|----------------------------------|  
|Managed 應用程式 (「自我裝載」)|在開發期間使用的主控台應用程式。<br />豐富型 WinForm 和[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]存取服務的用戶端應用程式。|-有彈性。<br />-容易部署。<br />-不企業解決方案的服務。|  
|Windows 服務 (之前稱為 NT 服務)|-長時間執行[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]IIS 外部裝載的服務。|服務處理序存留期間由作業系統在非訊息啟動。<br />支援所有版本的 Windows。<br />安全的環境。|  
|IIS 5.1、 [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-執行[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務與並存[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]透過 HTTP 通訊協定在網際網路上的內容。|同處理序回收。<br />-閒置關機。<br />-處理狀況監控。<br />訊息型啟用。<br />-僅限 HTTP。|  
|Windows Process Activation Service (WAS)|-執行[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務使用不同的傳輸通訊協定在網際網路上未安裝 IIS。|不需要 IIS。<br />同處理序回收。<br />-閒置關機。<br />-處理狀況監控。<br />訊息型啟用。<br />-使用 HTTP、 TCP、 具名的管道和 MSMQ。|  
|IIS 7.0|-執行[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]內容。<br />-執行[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]使用各種不同的傳輸通訊協定在網際網路上的服務。|-已優點。<br />-整合與[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]和 IIS 內容。|  
  
 裝載環境的選擇取決於用來部署該環境的 Windows 版本、用來傳送訊息所需的傳輸，以及所需的處理序類型和應用程式定義域回收。 下表摘要說明與這些需求相關的資料。  
  
|裝載環境|平台可用性|支援的傳輸|處理序和 AppDomain 回收|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Managed 應用程式 (「自我裝載」)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|否|  
|Windows 服務 (之前稱為 NT 服務)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|否|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|是|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|是|  
|Windows Process Activation Service (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|是|  
  
 從未受信任的主機執行服務或任何延伸項目都會破壞安全性，這點請您務必注意。 同時，請注意當您開啟模擬下的 <xref:System.ServiceModel.ServiceHost> 時，應用程式必須確定使用者尚未登出，例如，藉由快取使用者的 <xref:System.Security.Principal.WindowsIdentity> 來判斷。  
  
## <a name="see-also"></a>另請參閱  
 [系統需求](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [如何：在 IIS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [如何：在 WAS 中裝載 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [如何： 將 WCF 服務裝載於 Managed 的 Windows 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [如何：於受管理的應用程式中裝載 WCF 服務](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
