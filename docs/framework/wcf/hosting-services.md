---
title: 裝載服務
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: 4342b3d6219f0c996264bb7ed190b1204338ba64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051152"
---
# <a name="hosting-services"></a>裝載服務
如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。 Windows Communication Foundation (WCF) 服務專為在支援 managed 程式碼在任何 Windows 處理程序中執行。  
  
 WCF 會提供統一的程式設計模型建置服務導向應用程式。 這個程式設計模型會維持一致並與部署服務的執行階段環境互相獨立。 實務上，這意味著不管裝載選項為何，服務的程式碼看起來都差不多。  
  
 這些裝載選項的範圍從在主控台應用程式中執行到伺服器環境 (例如，在由網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 管理的背景工作處理序中執行的 Windows 服務) 不一而足。 開發人員可選擇滿足服務部署需求的裝載環境。 這些需求可能源自部署了應用程式的平台、應用程式必須賴以傳送與接收訊息的傳輸，或是用來確保足夠可用性所需的處理序回收類型與其他處理序管理，或是其他一些管理或可靠性需求。 下節將提供有關裝載選項的資訊與指引。  
  
## <a name="hosting-options"></a>裝載選項  
  
#### <a name="self-hosting-in-a-managed-application"></a>在 Managed 應用程式中自我裝載  
 可以在任何受管理的應用程式中裝載 WCF 服務。 這是最彈性的選項，因為它只需要最少的基礎結構就可部署。 您可以將服務的程式碼嵌入 Managed 應用程式程式碼中，然後建立並開啟 <xref:System.ServiceModel.ServiceHost> 的執行個體以便提供服務。 如需詳細資訊，請參閱[如何：裝載 WCF 服務的受管理的應用程式中](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。  
  
 此選項可讓兩個常見案例：在主控台應用程式和豐富型用戶端應用程式，例如 Windows Presentation Foundation (WPF) 或 Windows Forms (WinForms) 為基礎執行的 WCF 服務。 裝載於主控台應用程式的 WCF 服務一般來說是很有用的應用程式開發階段。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。 這個裝載選項同時可讓豐富型用戶端應用程式 (例如， [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 和 WinForms 應用程式) 更容易與外界通訊。 例如，使用的對等共同作業用戶端[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]作為其使用者介面，也會裝載 WCF 服務，可讓其他用戶端連線，並共用資訊。  
  
#### <a name="managed-windows-services"></a>Managed Windows 服務  
 這個裝載選項包含註冊為受管理的 Windows 服務 （之前稱為 NT 服務） 裝載的 WCF 服務，如此一來服務處理序存留期由服務控制管理員 (SCM) 控制應用程式定義域 (AppDomain)Windows 服務。 就像自我裝載選項一樣，此類型的裝載環境要求將某些裝載程式碼撰寫成應用程式的一部分。 服務會實作為兩個 Windows 服務和 WCF 服務會讓它繼承自<xref:System.ServiceProcess.ServiceBase>類別，以及從 WCF 服務合約介面。 <xref:System.ServiceModel.ServiceHost> 接著會透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 方法來建立並開啟，並透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法加以關閉。 繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別必須同時實作，以允許藉由 Installutil.exe 工具將程式安裝為 Windows 服務。 如需詳細資訊，請參閱[如何：將 WCF 服務裝載於 Managed 的 Windows 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)。 受管理的 Windows 服務裝載選項所啟用的案例是，IIS 外部所裝載非訊息啟動的安全環境中的長時間執行 WCF 服務。 服務的存留期會改由作業系統來控制。 所有 Windows 版本都提供這個裝載選項。  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 IIS 裝載選項會與 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 整合並使用這些技術所提供的功能，例如處理序回收、閒置關機、處理序健康狀態監控，以及訊息啟動。 在 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 作業系統中，建議您採用這個解決方案來裝載必須具備高度可用性與高度擴充性的 Web 服務應用程式。 IIS 同時提供整合式管理功能，而這也是客戶希望從企業級伺服器產品中所得到的功能。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 如需有關如何設定 IIS 裝載的 WCF 服務，請參閱[How to:將 WCF 服務裝載於 IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
 請注意，IIS 裝載的服務只能使用 HTTP 傳輸。 它在 IIS 5.1 版的實作方式已經為 [!INCLUDE[wxp](../../../includes/wxp-md.md)]帶來一些限制。 在上提供 WCF 服務的 IIS 5.1 訊息式啟動[!INCLUDE[wxp](../../../includes/wxp-md.md)]封鎖其他所有自我裝載的 WCF 服務使用連接埠 80 來通訊的相同電腦上。 WCF 服務可以執行相同的 AppDomain/應用程式集區/背景工作處理序時由其他應用程式中[!INCLUDE[iis601](../../../includes/iis601-md.md)]上[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]。 但是因為 WCF 及[!INCLUDE[iis601](../../../includes/iis601-md.md)]兩者都使用核心模式 HTTP 堆疊 (HTTP.sys)，[!INCLUDE[iis601](../../../includes/iis601-md.md)]可以與其他不同於 IIS 5.1 的同一部電腦上執行的自我裝載 WCF 服務共用連接埠 80。  
  
#### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)  
 Windows Process Activation Service (WAS) 是 [!INCLUDE[lserver](../../../includes/lserver-md.md)] 上全新的處理序啟動機制 ( [!INCLUDE[wv](../../../includes/wv-md.md)]也提供此機制)。 它包含熟悉的 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 處理序模型 (應用程式集區和訊息處理序啟用) 和裝載功能 (例如，快速故障防護、健康狀態監控，與回收機制)，但是從啟用架構中移除對 HTTP 的相依性。 [!INCLUDE[iisver](../../../includes/iisver-md.md)] 會使用 WAS，以完成透過 HTTP 的訊息啟用。 WCF 的其他元件也可外掛至 WAS 以提供訊息型啟用，透過 WCF 支援其他通訊協定，例如 TCP、 MSMQ 及具名的管道。 如此便可讓使用通訊協定的應用程式使用 IIS 功能，例如處理序回收、快速故障防護，以及只提供給以 HTTP 為基礎的應用程式使用的常見組態系統等。  
  
 這個裝載選項要求必須正確設定 WAS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 如需有關如何設定 WAS 裝載，請參閱[How to:將 WCF 服務裝載於 WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)。  
  
## <a name="choosing-a-hosting-environment"></a>選擇裝載環境  
 下表將摘要說明一些與各個裝載選項相關的主要優點與案例。  
  
|裝載環境|常見案例|主要優點與限制|  
|-------------------------|----------------------|----------------------------------|  
|Managed 應用程式 (「自我裝載」)|在開發期間使用的主控台應用程式。<br />-豐富型 WinForm 和[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]存取服務的用戶端應用程式。|富彈性。<br />簡單部署。<br />-不企業解決方案的服務。|  
|Windows 服務 (之前稱為 NT 服務)|-長期執行的 WCF 服務 IIS 外部所裝載。|服務控制作業系統，在非訊息啟動的處理序存留期。<br />支援所有版本的 Windows。<br />安全的環境。|  
|IIS 5.1、 [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-執行 WCF 服務與並存[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]使用 HTTP 通訊協定在網際網路上的內容。|同處理序回收。<br />-閒置關機。<br />-處理序健全狀況監視。<br />-訊息型啟用。<br />-僅限 HTTP。|  
|Windows Process Activation Service (WAS)|-執行而不需要使用各種傳輸通訊協定在網際網路上安裝 IIS 的 WCF 服務。|不需要 IIS。<br />同處理序回收。<br />-閒置關機。<br />-處理序健全狀況監視。<br />-訊息型啟用。<br />-使用 HTTP、 TCP、 具名的管道和 MSMQ。|  
|IIS 7.0|-執行 WCF 服務使用[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]內容。<br />-使用各種傳輸通訊協定在網際網路上執行的 WCF 服務。|-已優點。<br />-整合了[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]和 IIS 內容。|  
  
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

- [系統需求](../../../docs/framework/wcf/wcf-system-requirements.md)
- [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)
- [如何：裝載在 IIS 中的 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [如何：裝載在 WAS 中的 WCF 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [如何：將 WCF 服務裝載於 Managed 的 Windows 服務](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [如何：裝載 WCF 服務中的受管理的應用程式](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
