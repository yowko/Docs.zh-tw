---
title: 支援的部署案例
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 5be9ab3d300da2095a45846d334512382b4067f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743459"
---
# <a name="supported-deployment-scenarios"></a>支援的部署案例

支援在部分信任的應用程式中使用的 Windows Communication Foundation （WCF）功能子集，是為了符合使用 WCF 之部分（但非全部）案例的需求而設計的。 在伺服器上，WCF 符合網際網路規模共用主機服務提供者的需求，這些是基於安全性考慮，在 ASP.NET 2.0 中級信任許可權集合中執行協力廠商應用程式。 在用戶端上，WCF 部分信任支援主要是為了符合[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或 WPF 的 XAML 瀏覽器應用程式技術之類的部署技術需求，這種方式可讓您從不受信任的網站進行無縫且安全的桌面應用程式部署。

## <a name="minimum-permission-requirements"></a>最低許可權需求

WCF 支援應用程式中以下列任一標準命名許可權集合執行的功能子集：

- 中度信任權限

- 網際網路區域權限

嘗試在部分信任的應用程式中使用具有更嚴格許可權的 WCF，可能會在執行時間導致安全性例外狀況。

如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。

## <a name="partial-trust-on-the-server"></a>伺服器上的部分信任

許多 ASP.NET Web 應用程式裝載服務的商業提供者，會要求在其伺服器上執行的應用程式會在 ASP.NET 2.0 Medium Trust 許可權集合中執行。 WCF 服務可以在這些環境中執行，前提是它們會使用 <xref:System.ServiceModel.BasicHttpBinding>、<xref:System.ServiceModel.WebHttpBinding>或具有傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。

在中等信任裝載環境中執行的 WCF 服務也可以藉由將訊息傳送至其他伺服器來回應用戶端要求，以作為中介層服務。 如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。

除了使用其中一個支援的 SOAP 系結來進行 SOAP 訊息處理之外，WCF 還支援在部分信任的應用程式中建立 Web 樣式服務的 <xref:System.ServiceModel.WebHttpBinding>。 Wcf [WEB HTTP 程式設計模型](wcf-web-http-programming-model.md)、 [wcf](wcf-syndication.md)新聞訂閱和[AJAX 整合以及 wcf 的 JSON 支援](ajax-integration-and-json-support.md)功能，在部分信任中都受到支援。

工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。

如需詳細資訊，請參閱[如何：在 ASP.NET 2.0 中使用中度信任](https://docs.microsoft.com/previous-versions/msp-n-p/ff648344(v=pandp.10))。

## <a name="partial-trust-on-the-client"></a>用戶端上的部分信任

在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)和 WPF 的 XAML 瀏覽器應用程式（XBAP）技術都使用部分信任將有限的許可權（網際網路區域）授與不受信任的程式碼。

您可以使用 WCF，從[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或 XBAP 所部署的部分信任應用程式中，與遠端伺服器通訊。 網際網路區域許可權集合包含來源主機的 <xref:System.Net.WebPermission>，可讓這些應用程式使用[部分信任功能相容性](partial-trust-feature-compatibility.md)中所述的任何支援的 WCF 系結，與源伺服器進行通訊。

## <a name="see-also"></a>另請參閱

- [程式碼存取安全性](../../misc/code-access-security.md)
- [Windows Presentation Foundation 瀏覽器裝載的應用程式總覽](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [部分信任](partial-trust.md)
- [ASP.NET 信任層級和原則檔案](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))
