---
title: 裝載服務
description: 瞭解 WCF 服務的裝載選項。 服務必須裝載于建立該服務的執行時間環境中，並控制其內容和存留期。
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: 41a7a3e651d234de4079455a667df670d6c7435d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294647"
---
# <a name="hosting-services"></a>裝載服務

如果要成為作用中的服務，必須將服務裝載在建立及控制其內容和存留時間的執行階段環境中。 Windows Communication Foundation (WCF) 服務是設計來在任何支援 managed 程式碼的 Windows 進程中執行。

WCF 提供統一的程式設計模型來建立服務導向應用程式。 這個程式設計模型會維持一致並與部署服務的執行階段環境互相獨立。 實務上，這意味著不管裝載選項為何，服務的程式碼看起來都差不多。

這些裝載選項的範圍從在主控台應用程式中執行到伺服器環境 (例如，在由網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 管理的背景工作處理序中執行的 Windows 服務) 不一而足。 開發人員可選擇滿足服務部署需求的裝載環境。 這些需求可能源自部署了應用程式的平台、應用程式必須賴以傳送與接收訊息的傳輸，或是用來確保足夠可用性所需的處理序回收類型與其他處理序管理，或是其他一些管理或可靠性需求。 下節將提供有關裝載選項的資訊與指引。

## <a name="hosting-options"></a>主機選項

### <a name="self-host-in-a-managed-application"></a>受控應用程式中的 Self-Host

 WCF 服務可以裝載在任何受控應用程式中。 這是最彈性的選項，因為它只需要最少的基礎結構就可部署。 您可以將服務的程式碼嵌入 Managed 應用程式程式碼中，然後建立並開啟 <xref:System.ServiceModel.ServiceHost> 的執行個體以便提供服務。 如需詳細資訊，請參閱 [如何：在 Managed 應用程式中裝載 WCF 服務](how-to-host-a-wcf-service-in-a-managed-application.md)。

 此選項可啟用兩個常見的案例：在主控台應用程式中執行的 WCF 服務和豐富型用戶端應用程式，例如根據 Windows Presentation Foundation (WPF) 或 Windows Forms (WinForms) 的應用程式。 在應用程式的開發階段，在主控台應用程式中裝載 WCF 服務通常很有用。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。 此裝載選項也可讓豐富型用戶端應用程式（例如 WPF 和 WinForms 應用程式）輕鬆與外界通訊。 例如，對等共同作業用戶端，使用 WPF 做為其使用者介面，同時也裝載 WCF 服務，以允許其他用戶端與其連線並共用資訊。

### <a name="managed-windows-services"></a>Managed Windows 服務

此裝載選項包含註冊應用程式域 (AppDomain) 將 WCF 服務裝載為受管理的 Windows 服務 (之前稱為 NT 服務) ，以便服務的進程存留期是由服務控制管理員 (Windows 服務的 SCM) 所控制。 就像自我裝載選項一樣，此類型的裝載環境要求將某些裝載程式碼撰寫成應用程式的一部分。 服務會同時實作為 Windows 服務和 WCF 服務，方法是使它繼承自 <xref:System.ServiceProcess.ServiceBase> 類別以及 wcf 服務合約介面。 <xref:System.ServiceModel.ServiceHost> 接著會透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 方法來建立並開啟，並透過覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法加以關閉。 繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別必須同時實作，以允許藉由 Installutil.exe 工具將程式安裝為 Windows 服務。 如需詳細資訊，請參閱 [如何：在 Managed Windows 服務中裝載 WCF 服務](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)。 受管理的 Windows 服務裝載選項所啟用的案例，就是在非訊息啟動的安全環境中，裝載于 IIS 外部的長時間執行 WCF 服務。 服務的存留期會改由作業系統來控制。 所有 Windows 版本都提供這個裝載選項。

### <a name="internet-information-services-iis"></a>網際網路資訊服務 (IIS)

IIS 裝載選項會與 ASP.NET 整合，並使用這些技術所提供的功能，例如進程回收、閒置關機、進程健康情況監視，以及以訊息為基礎的啟用。 在 Windows XP 與 Windows Server 2003 作業系統上，這是裝載 Web 服務應用程式（必須高度可用且可高度擴充）的慣用解決方案。 IIS 同時提供整合式管理功能，而這也是客戶希望從企業級伺服器產品中所得到的功能。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 如需有關如何為 WCF 服務設定 IIS 裝載的詳細資訊，請參閱 how [to：在 iis 中裝載 Wcf 服務](./feature-details/how-to-host-a-wcf-service-in-iis.md)。

 IIS 託管的服務只能使用 HTTP 傳輸。 在 IIS 5.1 中執行的是在 Windows XP 中引進一些限制。 Windows XP 上的 IIS 5.1 為 WCF 服務提供的訊息型啟用會封鎖同一部電腦上的任何其他自我裝載 WCF 服務，使其無法使用埠80進行通訊。 當 Windows Server 2003 上的 IIS 6.0 裝載時，WCF 服務可以在與其他應用程式相同的 AppDomain/應用程式集區/背景工作進程中執行。 但因為 WCF 和 IIS 6.0 都使用核心模式 HTTP 堆疊 ( # A0) ，所以 IIS 6.0 可以與在同一部電腦上執行的其他自我裝載 WCF 服務共用埠80，與 IIS 5.1 不同。

### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)

Windows Process Activation Service (WAS) 是 windows Server 2008 的新進程啟用機制，也可在 Windows Vista 上取得。 它會保留熟悉的 IIS 6.0 進程模型 (應用程式集區和訊息型進程啟用) 和裝載功能 (例如快速失敗防護、健康情況監視和回收) ，但會從啟用架構中移除對 HTTP 的相依性。 IIS 7.0 使用 WAS 透過 HTTP 來完成訊息啟動。 額外的 WCF 元件也會插入，以透過 WCF 支援的其他通訊協定（例如 TCP、MSMQ 和具名管道）提供訊息型啟用。 如此便可讓使用通訊協定的應用程式使用 IIS 功能，例如處理序回收、快速故障防護，以及只提供給以 HTTP 為基礎的應用程式使用的常見組態系統等。

 這個裝載選項要求必須正確設定 WAS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 如需有關如何設定 WAS 裝載的詳細資訊，請參閱 [如何：在 was 中裝載 WCF 服務](./feature-details/how-to-host-a-wcf-service-in-was.md)。

## <a name="choose-a-hosting-environment"></a>選擇裝載環境

 下表將摘要說明一些與各個裝載選項相關的主要優點與案例。

|裝載環境|常見案例|主要優點與限制|
|-------------------------|----------------------|----------------------------------|
|Managed 應用程式 (「自我裝載」)|-在開發期間使用的主控台應用程式。<br />-存取服務的豐富 WinForm 和 WPF 用戶端應用程式。|柔性.<br />-輕鬆部署。<br />-不是適用于服務的企業解決方案。|
|Windows 服務 (之前稱為 NT 服務)|-在 IIS 外部裝載的長時間執行 WCF 服務。|-由作業系統控制的服務進程存留期，而不是由訊息啟用。<br />-所有 Windows 版本都支援。<br />-安全的環境。|
|IIS 5.1、IIS 6。0|-使用 HTTP 通訊協定與網際網路上的 ASP.NET 內容並存執行 WCF 服務。|-進程回收。<br />-閒置關機。<br />-進程健康情況監視。<br />-以訊息為基礎的啟用。<br />-僅限 HTTP。|
|Windows Process Activation Service (WAS)|-執行 WCF 服務，而不使用各種不同的傳輸通訊協定在網際網路上安裝 IIS。|-不需要 IIS。<br />-進程回收。<br />-閒置關機。<br />-進程健康情況監視。<br />-以訊息為基礎的啟用。<br />-適用于 HTTP、TCP、具名管道和 MSMQ。|
|IIS 7.0|-使用 ASP.NET 內容執行 WCF 服務。<br />-使用各種不同的傳輸通訊協定在網際網路上執行 WCF 服務。|-有其優點。<br />-與 ASP.NET 和 IIS 內容整合。|

 裝載環境的選擇取決於用來部署該環境的 Windows 版本、用來傳送訊息所需的傳輸，以及所需的處理序類型和應用程式定義域回收。 下表摘要說明與這些需求相關的資料。

|裝載環境|平台可用性|支援的傳輸|處理序和 AppDomain 回收|
|-------------------------|---------------------------|--------------------------|-------------------------------------|
|Managed 應用程式 (「自我裝載」)|Windows XP、Windows Server 2003、Windows Vista、<br /><br /> Windows Server 2008|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|No|
|Windows 服務 (之前稱為 NT 服務)|Windows XP、Windows Server 2003、Windows Vista、<br /><br /> Windows Server 2008|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|No|
|IIS 5.1|Windows XP|HTTP|Yes|
|IIS 6.0|Windows Server 2003|HTTP|Yes|
|Windows Process Activation Service (WAS)|Windows Vista、Windows Server 2008|HTTP、<br /><br /> net.tcp、<br /><br /> net.pipe、<br /><br /> net.msmq|Yes|

 從未受信任的主機執行服務或任何延伸項目都會破壞安全性，這點請您務必注意。 此外，在模擬下開啟時 <xref:System.ServiceModel.ServiceHost> ，應用程式必須確保使用者不會登出，例如藉由快取使用者的來進行登入 <xref:System.Security.Principal.WindowsIdentity> 。

## <a name="see-also"></a>另請參閱

- [基本程式設計週期](basic-programming-lifecycle.md)
- [實作服務合約](implementing-service-contracts.md)
- [作法：在 IIS 中裝載 WCF 服務](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [作法：在 WAS 中裝載 WCF 服務](./feature-details/how-to-host-a-wcf-service-in-was.md)
- [作法：在受控的 Windows 服務中裝載 WCF 服務](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [作法：在受控應用程式中裝載 WCF 服務](how-to-host-a-wcf-service-in-a-managed-application.md)
